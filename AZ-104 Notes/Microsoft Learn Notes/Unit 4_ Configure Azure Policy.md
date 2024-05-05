# AZ-104 Notes

## Create Management Groups

- Azure management groups provide a level of scope and control above your subscriptions. Use manage groups as containers to manage access, policy, and compliance across your subscriptions  
    <br/>

## Things to know about management groups

- By default, all new subs are placed under the top-level management group, or **root group**
- All subs within a management group automatically inherit the conditions applied to that management group
- A management group tree can support up to six levels of depth
- Azure role-based access control authorization for management group operations isn't enabled by default  
    <br/>

## Things to consider when using management groups

- **Consider custom hierarchies and groups**
- **Consider policy inheritance**
- **Consider compliance rules**
- **Consider cost reporting**  
    <br/>

## Things to know about Azure Policy

- Main advantage of Azure Policy are in the areas of enforcement and compliance, scaling, and remediation.

![Screenshot 2024-03-25 103228.png](./_resources/Screenshot%202024-03-25%20103228.png)  
<br/>

## Things to consider when using Azure Policy

- **Consider deployable resources**
- **Consider location restrictions**
- **Consider rules enforcement**
- **Consider inventory audits**  
    <br/>

## Create Azure policies

- A *policy definition* describes the compliance conditions for a resource, and the actions to complete when the conditions are met.
- One or more policy definitions are grouped into an *initiative definition*, to control the scope of your policies and evaluate the compliance of your resources.  
    <br/>

## Four basic steps to create and work with policy definitions

1.  Create Policy definitions
2.  Create an initiative definition
3.  Scope the initiative definition
    - you can limit the scope of this to a specific management group, subscription, or resource groups
4.  Determine compliance
    - Individual resources, resource groups, and subscriptions within a scope can be exempted from having the policy rules affect it. Exclusions are handled individually for each assignment