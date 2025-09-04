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
- Click on **System** > **Identity Providers**  
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
- Select **Relying Party Trusts** > **Add Relying Party Trust**  
- In the wizard:  
  - Select **Claim aware** and click **Start**  
  - Select **Enter data about the relying party manually** and click **Next**  
  - Enter a **Display name** and click **Next**  
  - (Optional) Add the Encryption Certificate from Step 2 and click **Next**  
  - Enable support for the **SAML 2.0 WebSSO protocol** and enter the **ACS URL**  
  - Enter the **SP Entity ID** as the relying party trust identifier, click **Add**, then **Next**  
  - Choose an **Access Control Policy** (e.g., Permit everyone or Permit specific groups) and add AD Groups as needed  
  - Verify details and click **Next**  
  - Finish and select **Configure claims issuance policy for this application** before closing  

![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_1.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_2.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_3.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_4.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_5.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_6.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_7.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_8.png)  
![Create Relying Party Trust](img/adfs/adfs_relying_party_trust_9.png)

---

## Step 6: Add Claims for Relying Party Trust

- Select the newly created relying party trust  
- Go to **Actions** > **Edit Claim Issuance Policy**  
- In **Issuance Transform Rules**, click **Add Rule**  

**LDAP Attributes as Claims**  
- Claim rule name: enter a name  
- Attribute store: **Active Directory**  
- Map attributes:  
  - **E-Mail-Addresses** (or **User-Principal-Name**) → **E-Mail Address**  
  - **Token-Groups - Unqualified Names** → **Group**  

**Transform Incoming Claim: NameID**  
- Claim rule name: enter a name  
- Incoming claim type: **E-Mail Address**  
- Outgoing claim type: **Name ID**  
- Outgoing Name ID format: **Email**  
- Select **Pass through all claim values**  

**Transform Incoming Claim: Group Attribute**  
- Claim rule name: enter a name  
- Incoming claim type: **Group**  
- Outgoing claim type: **Group Attribute Statement Name** from Step 2  
- Select **Pass through all claim values**  

Click **Apply** and **OK** to save.  

![Configure Claims](img/adfs/adfs_configure_claim_1.png)  
![Configure Claims](img/adfs/adfs_configure_claim_2.png)  
![Configure Claims](img/adfs/adfs_configure_claim_3.png)  
![Configure Claims](img/adfs/adfs_configure_claim_4.png)  
![Configure Claims](img/adfs/adfs_configure_claim_5.png)  
![Configure Claims](img/adfs/adfs_configure_claim_6.png)  
![Configure Claims](img/adfs/adfs_configure_claim_7.png)  
![Configure Claims](img/adfs/adfs_configure_claim_8.png)  
![Configure Claims](img/adfs/adfs_configure_claim_9.png)  
![Configure Claims](img/adfs/adfs_configure_claim_10.png)

---

## Step 7: Configure Groups in Console

- Create groups in the console with the same names as the Active Directory groups  
- Map groups to projects with the appropriate privileges  

Example:  
- AD group **OrgAdminUsers** → configured as **Organization Admin** with access to all projects  

User lifecycle management is offloaded to ADFS:  
- **No Local Users** are required in these groups  
- **IdP Users** are automatically managed through ADFS  

![Assign Groups](img/adfs/group_adfs.png)  
![Users in Group](img/adfs/group_adfs_no_users_01.png)  
![Users in Group](img/adfs/group_adfs_no_users_02.png)


You have successfully enabled SSO with ADFS. Users can now log in using their ADFS credentials.  

---
