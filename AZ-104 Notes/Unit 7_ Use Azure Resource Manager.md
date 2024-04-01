# AZ-104 Notes

## Azure Resource Manager

- Azure resource manager provides several benefits:
    - You can deploy, manage, monitor all resource for you solution as a group
    - You can repeatedly deploy your solution throughout the development lifecycle and have confidence your resources are deployed in a consistent state
    - Manage your infrastructure through declarative templates rather than scripts
    - Can define the dependencies between resource so they are deployed in the correct order
    - Can apply access control to all services in your resource group because RBAC is natively integrated into the management platform
    - Can apply tags to resource to logically organize all the resources in your subscription
    - You can clarify your organization's billing by viewing costs for a group of resources sharing the same tag  
        <br/>

## Azure resource terminology

- *Resource* - A manageable item that is available through Azure. Some common resources are a **VM, storage account, web app, database, and Virtual Network.**
- *Resource group* - a container that holds related resources for an Azure solution.
- *Resource provider* - A service that applies the resource you can deploy and manage through Resource Manager. Some common resource providers are **Microsoft.Compute**, which supplies the VM resource, **Microsoft.Storage**, which supplies the storage account resource, and **Microsoft.Web**, which supplies resources related to webapps
- *Template* - a JSON file that defines one or more resources to deploy to a resource group. Also defines dependencies between the deployed resources. The template can be used to deploy the resources consistently and repeatedly
- *Declarative syntax* - Syntax that lets you state "Here is what I intend to create" without having to write the sequence of programming commands to create it. The **Resource Manager template** is an example. In the file you define the properties for the infrastructure to deploy to Azure  
    <br/>

## Resource Groups

- Resource groups cannot be renamed
- a Resource Group can contain resources that reside in a different region
- A resource can interact with resources in other resource groups  
    <br/>

## Create Azure Resource Manager locks

- Can create locks to prevent accidental deletion of resources in Azure
    - You can associate the lock with a subscription, resource group, or resource
    - Locks are inherited by child resources  
        <br/>

## Lock types

- There are two types of resource locks
    - **Read-Only locks**, which prevent any changes to the resource
    - **Delete locks**, which prevent deletion  
        <br/>

## Remove resources and resource groups

- PowerShell command to delete resource groups
    - `Remove-AzResourceGroup - Name "Resourcegroupname"`