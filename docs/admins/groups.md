---
title: Product Security - Groups
description: Official Rafay product documentation. Explore "Product Security - Groups" docs and more here. Rafay is a SaaS-first Kubernetes Operations Platform with enterprise-class scalability.
tags:
  - Group
  - User Group
---


A group is a collection of users that have the same role or roles. Groups make it easier to manage users that are similar instead of managing users one at a time.

---

## Default Groups

All Organizations come primed with two default groups.

- All Local Users (All users that are managed locally in the Org belong to the "All Local Users" group. This group has the least privileges in the platform)

- Organization Admins (Users that belong to this group have access to ALL PROJECTS and is the most privileged role)


![All Local Users](img/groups/default_group.png)

---

## Add/Remove Users

Admins can easily add/remove users from Groups.

- Select one Group and click **Add/Remove Members**. Based on the requirement, add/remove local users or IDP users to the group

![Add/Remove Users from Group](img/groups/addremove_users_step1.png)

- Select the required users and click **Add to Group** from the left pane. This will add the users to the right pane **Group Users**
- **Save & Exit**. Once the users are added to the group, they will automatically inherit the roles associated with the group.

![Add/Remove Users from Group](img/groups/addremove_users_step2.png)


---

## Assign Groups to Projects

In the example below, we have a Project called "SolutionsTeam". We have created a Group called "DemoAdmin" who are meant to be the group of privileged users for this Project.

Instead of assigning users "one at a time", we will assign the "DemoAdmin" Project to the group called "SolutionsTeam"

![Assign Groups to Projects](img/groups/assign_group_to_project.png)

- Click on "Assign Group to Project"
- Select the Project from the drop down
- Select the Role Association, [Base Roles](./roles.md) (RBAC roles) (or) [Custom Roles](./custom_roles.md) and click **Save & Exit**

An example of selecting "Workspace Admin" base role from the list is given below. Permissions shows the privileges allowed for each role

![Assign Groups to Projects](img/groups/groupproject_role.png)

An example of selecting custom role from the drop-down is given below. Namespace is mandatory if assigning a custom role

![Assign Groups to Projects](img/groups/customabac_role.png)

Organization Admins can model similar structures using groups.

!!! Important
    Namespace selection is mandatory when assigning Namespace Admin or Namespace Read Only role to the groups. This requirement applies to both base roles and custom roles.

Admins can modify custom roles assigned to groups holding base roles of Namespace Admin and Namespace Read Only.

![Assign Groups to Projects](img/groups/edit_groups.png)


---

## Review Group

Admins can also review the users and projects associated with a group.

In the example below, we plan to review the users and projects associated with the Group "DemoAdmin"

- In the users tab, notice that there is only one local user in this group

![Review Group - Users](img/groups/reviewgroup_step1.png)

To view the IDP users of this group, select **IDP Users** option. The below example shows one IDP User in this group

![Review Group - Users](img/groups/idp_users.png)

- In the projects tab, notice that there is only one project called "SolutionsTeam" associated with this group and the assigned role is that of an Infrastructure Admin (Base Role)

![Review Group - Users](img/groups/group_projects.png)

Visit [this page](https://docs.rafay.co/security/rbac/cli/) for Group Management via CLI.

---
