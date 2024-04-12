# AZ-104 Notes
## Azure Storage
- In Azure Storage there are three categories of data:
	- Structured data
	- Unstructured data
	- Virtual Machine data
		<br/>
![Screenshot 2024-04-09 192439.png](../_resources/Screenshot%202024-04-09%20192439.png)
		<br/>
- Azure Cosmos, Azure Table Storage, Azure SQL Database = **Structured data**
- Azure Data Lake Storage and Azure Blob Storage = **Unstructured data**
- Standard Storage are backed by HDD, cheaper option
- Premium Storage are backed by SDD, offers low-latency performance
- **NOTE:** You cannot convert a standard tier storage account to a premium tier storage account or vice versa. Must create a new storage account and copy the data.
		<br/>
## Azure Storage Services
- Azure storage offers four data services that can be accessed by using an Azure storage account:
	- **Azure Blob Storage (containers)**: Massively scalable object to store text and binary data
	- **Azure Files**: Managed file shares for cloud or on-prem deployments
	- **Azure Queue Storage**: Messaging store for reliable messaging between application components
	- **Azure Table Storage**: A service that stores nonrelational structured data (known as NoSQL data)
		<br/>
## Azure Blob Storage
- Optimized for storing massive amounts of unstructured (nonrelational) data, such as text and binary. It is ideal for:
	- Serving images or documents directly to a browser
	- Storing files for distributed access
	- Streaming video and audio
	- Storing data for backup and restore, disaster recovery, and archiving
	- Storing data for analysis by an on-prem or Azure-hosted service
<br/>
## Azure Files
- Just your normal file share that uses SMB or NFS protocols
<br/>
## Azure Queue Storage
- Used to store lists of messages to be processed asynchronously
<br/>
## Azure Table Storage
- Azure table storage is a service that stores non-relational structured data (NoSQL data) in the cloud, providing a key/attribute store with a schemaless design. 
<br/>
## Storage Account Types

![Screenshot 2024-04-09 210452.png](../_resources/Screenshot%202024-04-09%20210452.png)
<br/>
- All storage account types are encrypted by using Storage Service Encryption (SSE) for data at rest
<br/>
## Determine replication strategies
- Four ways to replicate data:
	- Locally redundant storage (LRS) - lowest cost, low durability, stores replicated data in the same area as your current data
	- Zone redundant Storage (ZRS) - replicates data across three storage clusters in a single region, each cluster is physically separated from the others
	- Geo-redundant Storage (GRS) - replicates data to a secondary region.
	- Geo-zone redundant Storage (GZRS)- Combines both GRS and ZRS
<br/>
## Knowledge check
- Storage account names must be globally unique because the name is used as part of the URI (Uniform resource Identifier) for API access.