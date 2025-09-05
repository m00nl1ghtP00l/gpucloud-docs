---
title: KOP Integrations - Google Workspace
description: Configure Single Sign-On (SSO) between your Organization and Google Workspace.
tags:
  - Admin
  - Identity Provider
  - SSO
  - Google Workspace
  - Authentication
  - User Management
  - Security
---

Follow the steps documented below to integrate your Organization and Google Workspace for Single Sign-On (SSO).

!!! important
    Only users with **Organization Admin** privileges can configure SSO in the Web Console.

---

## Step 1: Create IdP

- Login into the Web Console as an Organization Admin  
- Navigate to **System > Identity Providers**  
- Click **New Identity Provider**  
- Provide a name and select **Custom** from the **IdP Type** dropdown  
- Enter the **Domain** for which you would like to enable SSO  

!!! important
    Within an organization, the domain of an IdP cannot be reused for another IdP.  
    A domain existing in one organization can also be used in another organization (for one IdP in each).  

- Optionally, toggle **Encryption** if you wish to send/receive encrypted SAML assertions  
- Provide a name for the **Group Attribute Name**  
- Optionally, toggle **Include Authentication Context** if you wish to send/receive auth context information in assertion  
- Click **Save & Continue**  

![Create IDP](img/googleworkspace/idp-detail.png)

!!! important
    Encrypting SAML assertions is optional because privacy is already provided at the transport layer using HTTPS.  
    Encrypted assertions provide an additional layer of security ensuring that only the SP (organization) can decrypt the SAML assertion.

---

## Step 2: View SP Details

The IdP configuration wizard will display information you need to copy/paste into your Google Workspace configuration:

- Assertion Consumer Service (ACS) URL  
- SP Entity ID  
- Name ID Format  

![View SP Details](img/googleworkspace/sp_details.png)

---

## Step 3: Create App in Google Workspace

- Login into your Google Workspace as an Administrator  
- Select **Apps**  

![Create App Integration](img/googleworkspace/googleworkspace-create-app-1.png)

- Select **SAML apps** to create a new application  

![Create App Integration 2](img/googleworkspace/googleworkspace-create-app-2.png)

---

## Step 4: General Settings

- Select the **Add App** dropdown  
- Select **Add custom SAML app**  
- Provide an App Name for the Web Console  
- Click **Add** to add the application  

![General Settings 1](img/googleworkspace/googleworkspace-config1.png)

- Download IdP metadata by selecting **DOWNLOAD METADATA** under *Option 1: Download IdP metadata*  

![General Settings 2](img/googleworkspace/googleworkspace-config-2.png)

---

## Step 5: Configure SAML

- Copy/Paste the **Entity ID** from Step 2  
- Copy/Paste the **ACS URL** from Step 2 into the **Reply URL**  
- Copy/Paste the **ACS URL** from Step 2 into the **Sign on URL**  
- Set **Name ID** to **EMAIL**  
- Click **CONTINUE**  

![Configure SAML 1](img/googleworkspace/googleworkspace-config-saml2.png)

- Click **FINISH**  

![Configure SAML 2](img/googleworkspace/googleworkspace-config-saml3.png)

---

## Step 6: Create Group in Google Workspace

- In the Admin Console select **Groups**  

![Create Group 1](img/googleworkspace/groups-1.png)   

- Enter a group name and click **Next**. This same group will need to be configured in the Console.  

![Create Group 2](img/googleworkspace/create-group-1.png)

- Select the access type and click **Create Group**

![Create Group 3](img/googleworkspace/create-group-2.png)  

---

## Step 7: Assign User to Group in Google Workspace

- In the Admin Console select **Users**  

![Users 1](img/googleworkspace/users-1.png)  

- Select **Add to groups**  

![Users 2](img/googleworkspace/users2.png)  

- Add the user to the group created in Step 6  

![Users 3](img/googleworkspace/users3.png)

---

## Step 8: Enable SSO in Google Workspace

- Go to **Apps -> Web and mobile apps -> [Your SSO App] -> Service Status**  
- Set Service status to **ON for everyone**  
- Optionally, enable for a specific admin group by selecting groups  

![Enable 1](img/googleworkspace/enable1.png)

---

## Step 9: Configure SSO Attribute Mapping

The SSO Attribute Mapping step ensures Google Workspace sends the user’s group information as part of the SSO process.  

- Go to **Users > More > Manage custom attributes**  
- Select **ADD CUSTOM ATTRIBUTE**  
- Enter a Category (the name should match the **Group Attribute Statement Name** set in Step 1)  
- Set type to **Text**, Visibility to **Visible to User and admin**, and values to **Single Value**  

![Attribute Mapping](img/googleworkspace/attribute2.png)

- Go to **Apps > Web and mobile apps > [Your SSO App] > SAML Attribute mapping**  
- Select **Configure SAML attribute mapping**  
- Select **ADD MAPPING** and set:  
  - Google Directory attributes → custom field created above  
  - App attributes → **Group Attribute Name** from Step 1  

![Attribute Mapping](img/googleworkspace/attribute3.png)

---

## Step 10: Add Group Name to User in Google Workspace

- Go to **User Information** for the desired user account  
- Edit the attribute configured in Step 9  
- Set the value to the group name  

![Attribute User Mapping](img/googleworkspace/attribute4.png)

---

## Step 11: Specify IdP Metadata File

- Navigate back to the Web Console’s IdP Metadata Configuration page  
- Select **IdP Metadata File** and upload the file downloaded in Step 4  
- Save the IdP Settings  

![IdP 1](img/googleworkspace/idp1.png)

---

## Step 12: Create Group in Console

An identical named group must be created in the Console (same as the group in Step 6).  
Ensure this group is mapped to the appropriate Projects with the correct privileges.  

* Create a new group in the Console and select **CREATE**  

![Create Console Group 1](img/googleworkspace/create-console-group1.png)  
![Create Console Group 2](img/googleworkspace/create-console-group2.png)


You have successfully enabled SSO using Google Workspace.  
Organization members should now be able to log in to the Web Console using their Google Workspace credentials.

---
