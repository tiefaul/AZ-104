# AZ-104 Notes
## Azure Storage Security Strategies
- All data written to Azure Storage is automatically encrypted
- **Authentication** - Microsoft Entra ID and RABC are supported for Azure Storage for both resource management operations and data operations
- Data can be secured in transit between an application and Azure by using Client-Side Encryption, HTTPS, or SMB 3.0
- OS disks and data disks used by Azure VM can be encrpyted using **Azure Disk Encryption**
- **Shared Access Signatures (SAS)** - Delegated access to the data objects in Azure Storage can be granted by using a SAS
<br/>
## Create SAS
- A SAS is a uniform resource identifier (URI), it grants restricted access rights to Azure Storage resources. SAS is a way to share your resources without compromising account keys
- Can provide SAS to clients who should not have access to your storage account key. By giving SAS URI to these clients, you grant them access to a resource for a period of time.
<br/>
## Things to know about SAS
- Gives you control over the type of access you grant to clients who have the SAS
- An account level SAS can delegate access to multiple Azure Storage services, such as blobs, files, queues, and tables
- Specify the time interval for SAS validation
- Specifiy permissions granted by the SAS.
- SAS provides account level and service level control:
	- Account-Level SAS - Delegates access to resources in one or more Azure Storage Service
	- Service-Level SAS - Delegates access to a resource in only one Azure Storage service
- **Stored access policy** can provide a level of control when using SAS on the server side. Group SASs together and provide restrictions by using a stored policy.
- There are optional SAS configuration settings:
	- **IP addresses** - You can identify an IP address or range of IPs from which Azure Storage accepts the SAS. 
	- **Protocols** - You can specify the protocol over which Azure Storage accepts the SAS
<br/>
![Screenshot 2024-04-14 122950.png](./_resources/Screenshot%202024-04-14%20122950.png)
<br/>

## Identify URI and SAS parameters 
- When you create your SAS, a URI is created by using the parameters and tokens. The URI consists of your Azure Storage resource URI and the SAS token
- `https://myaccount.blob.core.windows.net/?restype=service&comp=properties&sv=2015-04-05&ss=bf&st=2015-04-29T22%3A18%3A26Z&se=2015-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=F%6GRVAZ5Cdj2Pw4tgU7IlSTkWgn7bUkkAg8P6HESXwmf%4B`
<br/>
![Screenshot 2024-04-14 123609.png](./_resources/Screenshot%202024-04-14%20123609.png)
<br/>


## Azure Storage Encryption
- All data written is encrypted through 256-bit AES
- Azure Storage encryption is enabled for all new and existing storage accounts and cannot be disabled
- You can manage keys yourself or have the keys be managed by microsoft. 
<br/>
## Customer-Managed Keys
- By creating your own keys, you have more flexibility and greater control
- You can create, disable, audit, rotate, and define access controls for your encryption keys
- Can be used with Azure Storage encryption. You can use a new key or an existing key vault and key. The Azure storage account and the key vault must be in the same region, but they can be in different subscriptions.
<br/>
## Knowledge Check 


![Screenshot 2024-04-14 140615.png](./_resources/Screenshot%202024-04-14%20140615.png)

