# AZ-104 Notes
## Things to know about user accounts
- Following table describes the user accounts in Entra ID


![Screenshot 2024-03-23 093411.png](./_resources/Screenshot%202024-03-23%20093411.png)

## Things to consider when choosing user accounts
- **Consider where users are defined**
	- Are they within the org?
	- Are they defined in external Entra instances?
	- Do you have users that are external to org?
- **Consider support for external contributors**
	- Allow external organizations access to your resources by using Guest Account type.
- **Consider a combination of user accounts**
	- Use Directory-Sync Identity for users in AD DS
	- Use Cloud Identities for users defined in your internal Entra structure or for users that are in a external Entra Instance 
		<br/>
## Manage User Accounts
- There are several ways to add clopud identity user accounts in Entra ID:
	- Azure portal
	- Microsoft 365 Admin Center
	- Microsoft Intune admin console
	- Azure CLI
		<br/>
## Things to know about cloud identity accounts
- A new user account must have a display name and a associated user account name.
	- **Display name example:**
		- Aran Sawyer-Miller
	- **User account name example:**
		- asawmill@contoso.com
- Information and settings that describe a user are stored in the user account profile
- The profile can have other settings like a user's job title, and their contact email address.
- A user with Gloval Admin or User admin priviledges can preset profile data in user accounts, such as the main phone number of the company
- Non-admin users can set some of their own profile data, but they can't change their display name or account name.
	<br/>
## Things to consider when managing cloud identity accounts
- **Consider user profile data**
	- this includes the user's picture, job, contact info, supply certain profile settings for each user. ***Allow them to do these things if neccessary***
- **Consider restore options for deleted accounts**
	- restoring for a deleted account are available up to 30 days after removal
- **Consider gathered account data**
	- Collect sign-in and audit log info for user accounts. Entra ID lets you gather this data
		<br/>
## Things to know about bulk account operations
- Entra ID lets you create and delete accounts in bulk
- Most common approach is to use Azure portal or Azure PowerShell


![Screenshot 2024-03-23 095505.png](./_resources/Screenshot%202024-03-23%20095505.png)

- Only Global admnin or User admins can create or delete accounts 
- Have to fill oout a CSV template of the data for the user accounts
- Bulk operation templates can be downloaded from the Entra Admin Center
- Bulk lists of user accounts can be downloaded
	<br/>
## Things to consider when creating user accounts
- **Consider naming conventions**
	- this can simplify the bulk create/delete process
- **Consider using initial passwords**
	- design a system to notify new users about their passwords in a secure way
- **Consider strategies for minimizing errors**
	- you can download a results file on the **Bulk Operations Results** page. This contains errors and reasons for them. Might tell you an account has been duplicated, etc.
		<br/>
## Creating Group Accounts
- Two different types of group accounts:
	- **Security groups:**
		- these are used to manage member and computer access to shared resources for a group of users
	- **Microsoft 365 groups:**
		- provide collab opportunities. group members can have access to shared mailboxes, calendars, files, sharepoint site, etc


![Screenshot 2024-03-23 101612.png](./_resources/Screenshot%202024-03-23%20101612.png)

- Use security groups to set permissions for groups, rather than addming permissions to each user
- Add Microsoft 365 groups to enable access for guest users outside of the Entra organization
- Security groups can be implemented only by a Entra admin
- Normal users and Entra admins can both use Microsoft 365 groups
	<br/>
## Things to consider when adding group members
- There are three different ways you can assign members access rights.
	- **Assigned:**
		- Add specific users as members of a group, where each user can have unique permissions
	- **Dynamic User:**
		- Use dynamic rules to automatically add and remove group members. When a member's attributes change, Azure reviews the dynamic group rules for the directory. If rule requirements are met, the member is added to the group, if not met then the user/member is removed
	- **Dynamic Device:**
		- (Security groups only) Apply dynamic group rules to automatically add and remove devices in security groups. If attributes change, Azure reviews, if rule requirements are met then the device is added to the security group, if not then the device is removed.
			<br/>
## Create administrative units
- Can be useful to restrict admin scope by using admin units 
- Things to consider:
	- **Consider management tools**
		- You can use Azure portal, PowerShell, cmdlets and scripts, or Microsoft Graph to manage your AUs
	- **Consider role requirements**
		- Plan your strategy for admin units according to roles of org. Only Global admins and Privilegede Role Admins can manage AUs
	- **Consider scope of admin units**
		- Give the admins what they need to perform admin duties and nothing else. They can use their default user permissions to browse other things outside of their admin unit
