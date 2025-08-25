---
title: Role based Access Control 
description: Control and Manage End User Access 
---

End users of are typically data scientists, ML researchers or developers. Once the Org Admin provides the user with the appropriate role, they will have the ability to login into the self service portal, create and  manage workspaces, request for GPUs, compute, deploy and operate Jupyter notebooks and other services made available by the administrator or service provider. 

--- 

## Access Control 

All end users have to authenticate before they can access the end user self service portal. 

### Authentication (Local vs SSO Users)

Org Admins can manage users locally in their Org. Local users are authenticated before they are provided access to the self service portal. Admins may require the end users to use Multi Factor Authentication (MFA) to strongly authenticate before they are given access. 

It is a security best practice and a recommendation for enterprises to integrate their Org with their corporate Identity Provider (IdP). This integration will help provide end users with a superior user experience (i.e. single sign on) and also centralize authentication of users. Please review the IdP Integration documentation for instructions on how to implement this.

### Authorization 

Authorization of user access to the self service portal is performed using Role assignments. If end users can successfully authenticate and demonstrate they have been assigned the necessary roles, they will be able to access their Self Service Portal. End users need to have a role assignment of either Data Scientist or ML Researcher or Developer. 

#### Groups

At scale, it will be impractical for admins to manage roles for every user on a 1x1 basis. It is a common and recommended practice to use **groups** as a way to streamline the management burden. For example, administrators can create a **group** called "data scientists" and assign the role "Data Scientist" to the group. With this approach, they just need to add a user to this group to onboard a new data scientist. 

!!! note
    Organizations that are unable to centralize group management in their Identity Provider can override authorization in their Orgs. The overrides can either augment or replace the authorization details for the user. 
