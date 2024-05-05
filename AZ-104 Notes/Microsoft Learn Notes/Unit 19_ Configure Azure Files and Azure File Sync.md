# AZ-104 Notes
## Comparing Azure Files to Blob Storage and Azure Disks
- The following table compares the different features that Azure Files, Blob Storage, and Azure Disks have.


![Screenshot 2024-04-17 182018.png](./_resources/Screenshot%202024-04-17%20182018.png)
<br/>
## Types of Azure File Shares
- There are two types of file shares:
	- Standard:
		- Can be used with SMB and REST protocol only, while premium file shares can be used with SMB, NFS, and REST protocols
	- Premium:
		- Stores data on modern SSDs, while the standard tier uses HDDs
- You can easily switch from hot, cool, and transaction optimized tiers of standard file shares, but you can't switch from premium file shares to any of the standard tiers
<br/>
- Azure Files has snapshots. It also takes a snapshot of individual files so you can revert a single object if needed
- Azure files aslo offers Soft Delete.
	- Soft delete is where you delete an object (by mistake or on purpose) and then if you decide you want it back, you can recover. Think of it as the recycle bin on windows.
	- Soft delete also has a retention period of up to 365 days
<br/>
## Azure Storage Explorer
- A standalone app that makes it easy to work with Azure Storage data on Windows, MAC, or Linux.
- Requires both management (Azure Resource Manager) and data layer permissions to allow full access to your resources. You need Azure AD permissions to access your storage account, the containers in your account, and the data in the containers.
- Azure Storage Emulator, let you connect to and manage local storage
- With Azure Storage Explorer you can use SAS (Shared access signature) to manage resource that belong to another subscription
- You can manage a specific Azure Storage service (blob container, queue, or table) that belongs to another Azure Subscription by using a SAS
- NOTE: **Cloud Tiering** allows frequently accessed files to be cached on the local server. Infrequently accessed files are tiered or archieved to the Azure file share according to the policy created. (Cloud tiering archives infrequently access files to free up space on the local file share)