# AZ-104 Notes

## Resource Manager template schema

- Azure Resource Manager templates are written in JSON

![Screenshot 2024-03-30 190922.png](./_resources/Screenshot%202024-03-30%20190922.png)

- $schema - (Required) Location of the JSON template
- contentVersion - (Required) Version of the template. You can provide any kind of value for this. This is for documentation purposes
- parameters - (Not Required) Values that are provided when deployment is executed to customize resource deployment
- Variables - (Not Required) Values that are used as JSON fragments in the template to simplify template language expressions
- Functions - (Not Required) User-defined functions that are available within the template
- Resources (Required) Resource types that are deployed or updated in a resource group
- Ouputs - (Not Required) Values that are returned after deployment  
    <br/>

## Resource Manager template parameters

![Screenshot 2024-03-30 192424.png](./_resources/Screenshot%202024-03-30%20192424.png)

- NOTE: You are limited to 256 parameters in a template. You can reduce the number of parameters by using objects that contain multiple properties  
    <br/>

## Bicep Templates

- **Azure Bicep** is a domain specific language (DSL) that uses declarative syntax to deploy Azure resources. It provides concise syntax, reliable type safety, and support for code reuse.
- You can use this instead of JSON to create your Resource Manager templates.
- It has reduce complexity compared to JSON