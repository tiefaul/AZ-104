 # AZ-104 Notes
## Entra ID
- Entra ID is a identity  Management Service
- Useful to give workforce seamless access to internal and external resources such as:
	- Internal resources amd apps located on corperate network
	- External resources like 365, Azure portal, and SaaS Apps
	- Cloud apps developed for organization
	<br/>
- Microsoft Entra Features:
	- SSO
	- Secure Remote Access
	- Ubiquitous device support
	- Cloud extensibility
	- Sensitive data protection
	- Self-Service Support
	<br/>
## Entra ID Concepts
- **Concepts** are the things you need to know in order to empliment Entra ID into your organization:
	- **Identity** - users, apps, servers that require authentication by using secret keys or certificates
	- **Account** - an identity that has data associated with it. Must have an identity before an account
	- **Microsoft Entra Account** - an Identity that is created through Entra ID or other cloud service. This account is also called a work or school account
	- **Azure Tenant** - a single dedicated and trusted instance of Entra ID. Each tenant (or directory) represtents a single org. When organization signs up for a Microsoft Cloud Service, a new tenant is created. You can create multiple tenants or instances. 
	- **Azure Subscription** - This is used to pay for Azure Cloud Services. Each subscription is joined to a single tenant. You can have multiple subscriptions. 
	<br/>
## Compare Active Directory Domain Services to Microsoft Entra ID
- Microsoft recommends that you us Entra ID instead of AD DS unless your configuration targets IaaS workloads that depend specifically on AD DS
- **Things to consider when using Microsoft Entra rather than AD DS:**
	- **Identity Solution** - AD DS is primarily a directory service, while ID is a full identity solution. ID is designed for internet-based applications that use HTTP/HTTPS communications. Features and capabilities of ID support a target strong identity management.
	- **Communication protocols** - ID does not use Kerberos Auth. ID implements HTTP/HTTPS protocols such as SAML, WS-Federation, and OpenID Connect for authentication (and OAuth for authorization)
	- **Federation Services** - Entra ID includes federation services, and many third-party services like Facebook
	- **Flat Structure** - Microsoft Entra users and groups are created in a flat structure. There are no OUs or group policy objects (GPOs)
	- **Managed Service** - In Entra ID, you only manage users, groups, and policies. AD DS can manage many other tasks, including deployment, configuration, VMs, patching, and other backend processes
	<br/>
## Select Microsoft Entra editions
- Entra ID comes in three editions:
	- Free
	- Premium P1
	- Premium P2
- Things to know about the different Editions:


![Screenshot 2024-03-22 141351.png](../_resources/Screenshot%202024-03-22%20141351.png)

- **Microsoft Entra ID Free**:
	- Provides user and group management, on-prem directory synchronization, and basic reports. SSO is supported across Azure, 365, and many popular SaaS apps.

- **Microsoft Entra ID P1**:
	- Includes the free features and lets your hybrid users access both on-prem and cloud resources. This edition supports advanced administration like dynamic groups, self-services group management, and cloud write-back capabilities. Includes Identity Manager, an on-prem identity and access management suite. Also allows self-service password reset for your on-prem users.

- **Microsoft Entra ID P2**:
	- Includes Free and P1 features. It offers Entra ID Protection to help provide risk-based Conditional Access to your apps and critical company data. Privileged Identity Management is included to help discover, restrict, and monitor administrators and their access to resources, and to provide just-in-time access when needed
	<br/>
## Implement Microsoft Entra self-service password reset
- SSPR (Self-Service password reset) gives users the ability to reset their own passwords
- **Things to know about the SSPR feature**:
	- Requires a Entra ID account with Global Admin Privileges to manage SPPR options. This account can always reset their own passwords, no matter what options are configured.
	- SSPR uses a security group to limit the users who have SSPR privileges.
	- All user accounts in your org must have a valid license to us SSPR
	<br/>
## Things to consider when using SSPR
- **Consider who can reset their passwords**. The SPPR feature has 3 options:
	- None
	- Selected
	- All
- The selected option is useful for creating groups who have SSPR enabled. You can create groups for testing or proof of concept before applying the feature to everyone/large group.
<br/>
- **Consider your authentication methods**:
	- Your system must require at least one authentication method to reset a password
	- Options include:
		- Email notification
		- Text message
		- Security code sent to user phone or office phone
		- Security questions
	- You can requre security questions to be registered for the users in your Entra Tenant
	- You can also set how many correctly answered security questions are required for password reset
	<br/>
## Knowledge Check 
1. What term defines a dedicated and trusted instance of Microsoft Entra ID?
	- Azure tenant 
