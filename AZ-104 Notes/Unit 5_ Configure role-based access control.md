# AZ-104 Notes

## Things you can do with RBAC (Role-Based Access Control)

- Allow an app to access all resources in a resource group
- Allow one user to manage VMs in a subscription, and allow another user to manage virtual networks
- Allow a database administrator (DBA) a group to manage SQL databases in a subscription.
- Allow a user to manage all resource in a resource group, such as VMs, websites, and subnets  
    <br/>

## Azue RBAC Concepts

![Screenshot 2024-03-26 191518.png](../_resources/Screenshot%202024-03-26%20191518.png)  
<br/>

## Create a role definition

- Role definitions consists of sets of permissions that are defined in a JSON file. Each permission has a name, such as *Actions* and *NotActions*
    - *Actions* permissions identify what actions are allowed
    - *Not Actions* permissions specify what actions aren't allowed
    - *DataActions* permissions indicate how data can be changed or used
    - *AssignableScopes* permissions list the scopes where a role definition can be assigned

![Screenshot 2024-03-26 200513.png](../_resources/Screenshot%202024-03-26%20200513.png)  
<br/>

## Create a role assignment

- A role assignment is the porcess of scoping a role definition to limit permissions for a requestor, such as a user, group, service principal, or managed identity.  
    <br/>

## Things to know about role assignments

- Purpose is to control access
- The scope limits which permissions defined for a role are available for the assigned requestor
- Access is revoked by removing a role assignment
- A resource inherits role assignments from its parent source
- The effective permissions for a requestor are a combination of the permissions for the requestor's assigned roles, and the permissions for the roles assigned to the requested resources  
    <br/>

## Things to consider when assigning scope levels for roles

![Screenshot 2024-03-26 202736.png](../_resources/Screenshot%202024-03-26%20202736.png)

- The diagram shows the following:
    - three security principals are supported: user, group, service principal
    - Six built-in roles and two custom roles are definede: Reader support tickets and VM operator
    - The contributor role has two sets of permissions: Actions, NotActions
    - The contributor is assigned a different scope to the Marketing and Pharma-sales resource groups:
        - Marketing users are granted access to create or manage any Azure resource in the Pharma-sales resource group
        - Marking users aren't granted access to resources outside the Pharma-sales resource group  
            <br/>

## Compare Azure roles to Microsoft Entra Roles

- Three types of roles are availbale for access management in Azure:
    - Classic sub admin roles
    - Azure RBAC roles
    - Microsoft Entra admin roles

![Screenshot 2024-03-26 203643.png](../_resources/Screenshot%202024-03-26%20203643.png)

- Microsoft Entra Admin roles are defined at the root level of the config, while Azure RBAC roles are defined for a requestor or resource at the root, management groups, subscriptions, resource groups, or resources levels.  
    <br/>

## Four fundamental Azure RBAC Roles

![Screenshot 2024-03-26 205113.png](../_resources/Screenshot%202024-03-26%20205113.png)

## Knowledge Check

- Remember that the contributor can read, write, delete. Just can't grant access to others
- Remeber that Azure roles are used to manage access to VMs, storage, and other resources. While Entra roles are used to manage access to Entra resources like user accounts and passwords.