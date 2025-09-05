---
title: KOP CLI - IDP (Identity Providers) Integration
description: Official product documentation for IDP integration using the KOP CLI.
tags:
  - CLI
  - Identity Provider
  - SSO
  - IDP Integration
  - Automation
---


The table below describes the list of actions performed on "IDP" using the RCTL CLI Utility.

| Resource  | Create |  Get  | Update  |Delete |
|-----------|--------|-------|--------|--------|
| IDP       | YES    | YES   | YES    | YES    |


---

Users are allowed to perform a focused automation approach for IDP integration.

## Create Identity Provider

Use the below command to create an Identity Providers

### With Encrypted SAML Assertion

```
./rctl create idp <idp-name> <idp-type> <domain-name> <group-name> --es
```

***Example***

```
./rctl create idp oktainteg okta okta.com oktadmins --es
```

***Output***

```
Success Creating IDP with name: okti
********* IMPORTANT *********
PLEASE SAVE BELOW URL TO CONFIGURE IDP METADATA
-----------------------------
Assertion Consumer Service URL (ACS / SP Identity URL) :
  https://hostname.com/auth/v1/sso/acs/123456-9e26-3232-123qwe456tyu/
Encryption Certificate content :
-----BEGIN CERTIFICATE-----
KSLGNKQ2FsaWZvcSGSLUAMIGSMQswCQYDVQQA1SFKSLGNKQ2FsaWA1S
FKSLGNKQ2FsaWZvcm5pYTESSKLGA1SFKSLGNKQ2FsaWZvcm5pYDAVS
bLbUQ3+iWq1CA0DFSGSLUA=
-----END CERTIFICATE-----
```


### Without Encrypted SAML Assertion

```
./rctl create idp <idp-name> <idp-type> <domain-name> <group-name>
```

***Example***

```
./rctl create idp demo-sso custom mydomain.io group1
```

***Output***

```
Success Creating IDP with name: demo-sso
********* IMPORTANT *********
PLEASE SAVE BELOW URL TO CONFIGURE IDP METADATA
-----------------------------
Assertion Consumer Service URL (ACS / SP Identity URL) :
  https://hostname.com/auth/v1/sso/acs/123456-9e87-5432-67890/
Group Attribute Statement Name:
```

---

## Get Identity Providers

Use the below commands to fetch the list of Identity Providers or a  single provider

### List All

```
./rctl get idp
```

***Output***

```
Idp Name      Idp Type   Domain Name    Encryption Status   Group Attribute Name
trial-idp3    Ping       mydomain3.co   true                group3
trial-idp2    Customer   mydomain2.co   false               group2
trail-idp1    Okta       mydomain1.co   false               group1
```

### Individual IdP

```
./rctl get idp <idpname>
```

***Example***

```
./rctl get idp google
```


***Output***

```
Idp Name: trial-idp3
Idp type: Ping
Domain Name: mydomain3.co
Encryption Status: true
Group Attribute Name : group3
```

---

## Update Identity Provider

Use the below commands to update the existing Identity Providers

### Using URL

```
./rctl update idp <idp-name> <url>
```

***Example***

```
./rctl update idp demo-sso https://mydomain.co/dev/qwertyuiop/sso/metadata
```

***Output***

```
Success UPDATING IDP metadata config with name: demo-sso
```

### Using File Upload

```
./rctl update idp <idp-name> upload <filepath>
```

***Example***

```
./rctl update idp demo-sso upload /platform/filename.xml
```

***Output***

```
Success UPLOADING IDP file: Updated for demo-sso
```

### Encrypted SAML Assertion Flag Enabled

```
./rctl update idp <idp-name> <idp-type> <domain-name> <group-name> --es
```

***Example***

```
./rctl update idp demo-sso okta oktadmins --es
```

***Output***

```
Success UPDATING IDP configuration
```


### Encrypted SAML Assertion Flag Disabled

```
./rctl update idp <idp-name> <idp-type> <domain-name> <group-name>
```

***Example***

```
./rctl update idp demo-sso custom mydomain.io group1
```

***Output***

```
Success UPDATING IDP configuration
```

---

## Delete Identity Provider

Use the below commands to delete the Identity Providers

### Listed Deletion

```
./rctl delete idp name1, name2, name3
```

### Single Deletion

```
./rctl delete idp <idp-name>
```

***Example***

```
./rctl delete idp demo-sso
```

---
