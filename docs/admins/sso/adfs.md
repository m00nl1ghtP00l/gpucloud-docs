---
title: ADFS Integration for Single Sign On
description: Steps for administrators to integrate Active Directory Federation Services (ADFS) with the platform for SSO.
tags:
  - ADFS
  - IdP
  - Single Sign On (SSO)
---

!!! important
	Only users with **Organization Admin** privileges can configure SSO.

---

## Step 1: Create Identity Provider

- Log in to the console as an Organization Admin  
- Click on **System** -> **Identity Providers**  
- Click on **New Identity Provider**  
- Provide a name, select **Custom** from the **IdP Type** dropdown  
- Enter the **Domain** for which SSO will be enabled  

!!! Important
	Within an organization, the domain of an IdP cannot be reused for another IdP.  
	A domain can exist in multiple organizations (once per IdP in each).  

- Enter the valid **Admin Email** for domain ownership validation  
- (Optional) Toggle **Encryption** if you want encrypted SAML assertions  
- Provide a name for the **Group Attribute Name**  
- (Optional) Toggle **Include Authentication Context** to send/receive auth context information in the assertion  
- Click **Save & Continue**  

![Create IdP](img/adfs/idp_detail.png)

!!! Important
	Encryption of SAML assertions is optional since HTTPS provides transport layer security.  
	Encrypted assertions add an additional layer of security by ensuring only the Service Provider can decrypt them.  

---

## Step 2: View Service Provider (SP) Details

The configuration wizard will show details to copy into your ADFS Relying Party Trust:

- Assertion Consumer Service (ACS) URL  
- SP Entity ID  
- Name ID Format  
- Encryption Certificate (if enabled)  
- Group Attribute Statement Name  
- Consumer Binding  

Click **Save & Continue**  

![View SP Details](img/adfs/sp_details.png)

---

## Step 3: Specify IdP Metadata

- Download the ADFS IdP Metadata file from:  
  `https://<your_adfs_hostname>/FederationMetadata/2007-06/FederationMetadata.xml`  
- On the **Metadata configuration** page, select **IdP Metadata File**  
- Use the **Upload** button to add the ADFS IdP Metadata file  
- Click **Save & Exit**  

![IdP Metadata](img/adfs/adfs_idp_metadata.png)

Once complete, you can view details about the IdP configuration on the **Identity Provider** page and update if required.  

---

## Step 4: Verify Domain

- The admin email provided in Step 1 will receive a **domain verification email**  
- Click the **EMAIL VERIFICATION LINK** in the email to verify the domain  
- Once verified, the status of the ADFS IdP can be confirmed on the **Identity Provider** page  

![Completed IdP](img/adfs/adfs_domain_verify_email.png)  
![Completed IdP](img/adfs/adfs_idp_complete.png)

---

## Step 5: Create Relying Party Trust in ADFS

- Open **AD FS Management**  
- Select **Relying Party Trusts** -> **Add Relying Party Trust**  
- In the wizard:  
    - Select **Claim aware** and click **Start**  
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_1.png)  

    - In Select Data Source windows, select **Enter data about the relying party manually** and click **Next**
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_2.png)  

    - Enter a **Display name** and click **Next**  
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_3.png)

    - (Optional) In Configure Certifcate windows, click **Browse** and select the Encryption Certificate (if encryption enabled) downloaded in Step 2 and click **Next**
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_4.png)

    - In Configure URL windows, select **Enable support for the SAML 2.0 WebSSO protocol** and enter the Assertion Consumer Service (ACS) URL from the SP configuration in Step 2 to the Relying party SAML 2.0 SSO service URL text field and click **Next**
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_5.png)  

    - Enter the **SP Entity ID** as the relying party trust identifier, click **Add**, then **Next**
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_6.png)

    - Choose an **Access Control Policy** (e.g., Permit everyone or Permit specific groups) and add AD Groups as needed

    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_7.png)

    - Verify details and click **Next**
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_8.png)

    - Finish and select **Configure claims issuance policy for this application** before closing
    ![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_9.png)

---

## Step 6: Add Claims for Relying Party Trust

- Select the newly created relying party trust  
- Go to **Actions** -> **Edit Claim Issuance Policy**
![Configure Claims](img/adfs/adfs_configure_claim_1.png)  

- In **Issuance Transform Rules**, click **Add Rule**  
![Configure Claims](img/adfs/adfs_configure_claim_2.png)

In **Add Transform Claim Rule Wizard > Choose Rule Type** windows, select Send LDAP Attributes as Claims in the Claim rule template and click **Next**

![Configure Claims](img/adfs/adfs_configure_claim_3.png)  

**Transform Incoming Claim: NameID**

- Claim rule name: enter a name  
- Select **Active Directory** for Attribute store
- Select LDAP Attribute **E-Mail-Addresses** (or User-Principal-Name if email is not configured for the user) to map as Outgoing Claim Type E-Mail Address
- Select LDAP Attribute **Token-Groups - Unqualified Names** to map as Outgoing Claim Type **Group**
- Then click **Finish** to create the LDAP attribute claim rule

![Configure Claims](img/adfs/adfs_configure_claim_4.png)

- In Issuance Transform Rules windows, click Add Rule to add the transform an incoming claim rule for NameID

![Configure Claims](img/adfs/adfs_configure_claim_5.png)

- In **Add Transform Claim Rule Wizard -> Choose Rule Type** windows, select **Transform an Incoming Claim** in the Claim rule template and click **Next**

![Configure Claims](img/adfs/adfs_configure_claim_6.png)  

- In Configure Claim Rule windows:
    - Enter **Claim rule name**
    - Select **E-Mail Address** for Incoming claim type
    - Select **Name ID** for Outgoing claim type
    - Select Email for **Outgoing name ID format**
    - Select **Pass through all claim values**
    - Then click **Finish** to create the transform an incoming claim rule for NameID

![Configure Claims](img/adfs/adfs_configure_claim_7.png)  

- In **Issuance Transform Rules** windows, click **Add Rule** to add the transform an incoming claim rule for Group Attribute

![Configure Claims](img/adfs/adfs_configure_claim_8.png)

- In **Add Transform Claim Rule Wizard -> Choose Rule Type** windows, select Transform an Incoming Claim in the Claim rule template and click **Next**

![Configure Claims](img/adfs/adfs_configure_claim_9.png)

- In Configure Claim Rule windows:
    - Enter **Claim rule name**
    - Select **Group** for Incoming claim type
    - Enter the value of **Group Attribute Statement Name** from Step 2 for Outgoing claim type
    - Select **Pass through all claim values**
    - Then click **Finish** to create the transform an incoming claim rule for Group Attribute

![Configure Claims](img/adfs/adfs_configure_claim_10.png)

---

## Step 7: Configure Groups in Console

- Create groups in the console with the same names as the Active Directory groups  
- Map groups to projects with the appropriate privileges  

Example:

- AD group **OrgAdminUsers** → configured as **Organization Admin** with access to all projects  

![Assign Groups](img/adfs/group_adfs.png)

User lifecycle management is offloaded to ADFS:

- **No Local Users** are required in these groups

![Users in Group](img/adfs/group_adfs_no_users_01.png)

- **IdP Users** are automatically managed through ADFS  

![Users in Group](img/adfs/group_adfs_no_users_02.png)

You have successfully enabled SSO with ADFS. Users can now log in using their ADFS credentials.  

---
