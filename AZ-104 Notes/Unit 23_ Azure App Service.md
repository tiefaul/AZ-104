# AZ-104 Notes
## Azure App Service
- This brings together everything you need to create websites, mobile backends, and web APIs for any platform or device. 
- Some Azure App Service Benefits:


![Screenshot 2024-04-24 195141.png](../_resources/Screenshot%202024-04-24%20195141.png)
<br/>
## Post-creation settings
- Here are some extra application settings:
	- **Always On**: Keep your app loaded even when there's no traffic. This setting is required continuous WebJobs or for WebJobs that are triggered by using CRON expression.
	- **ARR Affinity**: In a multi-instance deployment, you can ensure your app client is routed to te same instance for the life of thhe session
	- **Connection strings**: Connection strings for your app are encrypted at rest and transmitted over an encrypted channel
<br/>
## Continuous integration and deployment
- Can connect your web app with Github or Azure DevOps, etc. and App Service will auto-sync your code and any future changes to the code into your web app.
- When you creat your web app with App Service, you can choose from automated or manual deployment:
	- **Automated deployment** (continuous integration) - is used to push out new features and bug fixes in a fast pattern with minimal impact on end users. You can use:
		- *Azure DevOps* - Can be used to build your own code in the cloud, run the tests, generate a release from the code, and push you r code to an Azure web app
		- *Github* - When you connect to your GitHub repo to Azure for automated deployment, any changes you push to your production branch are automatically deployed for you.
		- *BitBucket* - Similar to GitHub
	- **Manual deployment** - enables you to manually push your code to Azure. You can do this by:
		- *Git* - The App Service Web Apps feature offers a Git URL that you can add as a remote repo. Pushing to the remote repo deploys your app.
		- *CLI* - The `webapp up`  command is a feature of the CLI that packages your app and deploys it.
		- *Visual Studio* - Features a App Service deployment wizard that can walk you througfh the deployment process
		- *FTP/S* - is a traditional way of pushing you code to many hosting enviroments, including App Service.
<br/>
## Deployment Slots
- When pushing your web app, mobile backend, or API to Azure Service, you can use a separate deployment slot instead of the default production list
- Characteristics of deployment slots:
	- they are live apps that have their own hostnames
	- Available in Standard, Premium, and Isolated App Service pricing tiers
	- The tiers offer different numbers of deployment slots
	- App content and config elements can be swapped between two deployment slots, including the production slot
## Things to consider when using deployment slots
- **Consider validation** - You can validate changes to your app in a staging deployment slot before swapping the app changes with the content in the production slot
- **Consider reductions in downtime** - Deploying an app in a slot first and swapping it to production ensures the instance of the slot are up before being swapped into production. Elimates downtime and ensures seamless traffic redirection. Can be automated by configuring **Auto Swap** when pre-swap validation isnt needed.
- **Consider restoring to last known good site** - After swapping a slot with the staged app to the production app, the slot now has the previous production app. If the staged app that you made changes too isn't performing as expected, you can swap them immediately and return to your last know good site.
- **Consider auto swap** - This streamlines Azure DevOps scenarios where you want to deploy your app continuously with zero cold starts and zero downtime for app customers. When enabled on a slot into production, everytime you push your code changes to that slot, App Service automatically swaps the app into production after it is warmed up in the source slot. This is not currently supported for web apps on Linux
<br/>
## Azure Application Insights
- This lets you monitor your live apps
- Can integrate with App Service to detect performance anomalies in your apps
- Works on various platforms including .NET, Node.js and Java EE
- Integrates with your Azure DevOps process, and has connection points to many development tools
<br/>
## Knowledge Check
- When you clone a config from another deployment slot, **connection strings** follows the content across the swap.
- Connection strings are used to identify the server instance and database to connect to and to determine what driver, login, etc, to use to connect to an instance