# AZ-104 Notes
## Things to know about domain names in Azure
- When you create an Azure subscription, Azure automatically created a Microsoft Entra domain for your subscription
	- You must be a global admin to perform domain management tasks. The global admin is the user who created the subscription
- Azure applies an initial domain name to your initial domain instance
	- The initial domain name follows the form `<Your Domain Name>` followed by `.onmicrosoft.com`. For example, `yourdomainname.onmicrosoft.com`
- The purpose of the custom domain name is to provide a simplified form of your domain name to support specific users or tasks
- The initial domain name is intended to be used until your custom domain name is verified

