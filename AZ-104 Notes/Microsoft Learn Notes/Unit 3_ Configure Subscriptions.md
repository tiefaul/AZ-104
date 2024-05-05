# AZ-104 Notes

## Things to know about Microsoft Datacenter Regions

- Azure is available in more than 60 regions and 140 countries
- Azure has more global regions than any other cloud provider
- Regions provide you with the flexibility and scale needed to bring applications closer to your users
- Regions preserve data residency and offer comprehensive compliance and resiliency options for customers  
    <br/>

## Things to know about regional pairs

- Most regions are paired with another region within the same geography to make a **regional pair**. This helps support always-on availability
- The following table describes some paired regions:

![Screenshot 2024-03-23 134950.png](../_resources/Screenshot%202024-03-23%20134950.png)

## Things to consider when using regions and region pairs

- **Consider resource and region deployment**
- **Consider service support by region**
    - Some services are available only in certain regions, such as size and storage for VMs
- **Consider services that don't require regions**
    - Some services don't require you to select a region, like:
        - Microsoft Entra ID
        - Microsoft Azure Traffic Manager
        - Azure DNS
- **Consider exceptions to region pairing**
    - Check Azure website for current region availability and exceptions
- **Consider benefits of data residency**
    - Use the benefits of data residency offered by regional pairs. This feature can help meet requirements for tax and law enforcement jurisdiction purposes  
        <br/>

## Implement Azure Subscriptions

- An Azure subscription is a group of Azure services that is linked to an Azure Account. An Azure Account is an identity in Entra ID or a directory that is trusted by Entra ID, such as a work or school account.  
    <br/>

## Things to know about subscriptions

- Every Azure cloud service belongs to a subscription
- Each sub can have a different billings and payment config
- Multiple subs can be linked to the same Azure account
- More than one Azure account can be linked to the same sub
- Billing for Azure services is done on a per-sub basis
- If your Azure account is the only account associated with a sub, you are responsible for the billing requirements
- Programmatic operations for a cloud service might require a sub ID  
    <br/>

## Things to consider when using Subscriptions

- consider the types of Azure accounts required
- Consider multiple subs
- Consider a dedicated shared services sub
- Consider access to resources  
    <br/>

## Ways to obtain an Azure subscription

![Screenshot 2024-03-23 134950.png](../_resources/Screenshot%202024-03-23%20134950-1.png)  
<br/>

## Resource Tagging

- Tagging is useful to organize your resources
- Each tag has a **name** and a **value**
    - You can have the **name:** server and the **value:** production or development
- Tag name remains constant for all resources that have the tag applied
- The value can be selected from a defined set of values, or unique for a specific resource instance
- A resource or resource group can have a maximum of 50 tag name/value pairs
- Tags applied to a resource group aren't inherited by the resources in the resource group
- Tags can be useful for billing data, when using Microsoft Cost Management, you can export data via CSV and there is a tag filter  
    <br/>

## Apply Cost Savings

- Azure has several options for cost savings. These are the advantages:

![Screenshot 2024-03-23 151036.png](../_resources/Screenshot%202024-03-23%20151036.png)