# AZ-104

## Azure Blob Storage

- Is a service that stores *unstructured data* in the cloud as objects or blobs. It is also referred to as *object storage* or *container storage*.  
    <br/>

## Things to know about Blob Storage

- Can store any type of text or binary data. Examples are:
    - Text docs
    - Images
    - Video files
    - Application installers
- Uses three resources to store and manage your data:
    - An Azure storage account
    - Containers in an Azure storage account
    - Blobs in a container
- To implement Blob storage, you configure several settings:
    - Blob container options
    - Blob types and upload options
    - Blob storage access tiers
    - Blob lifecycle rules
    - Blob object replication options  
        <br/><br/>![Screenshot 2024-04-10 204038.png](./_resources/Screenshot%202024-04-10%20204038.png)  
        <br/>
- You can use Blob Storage to serve images or docs via a browser
- Can stream audio and video
- good for disaster recovery and archiving, backup and restore
- Can store data for analysis by an on-prem or Azure hosted service  
    <br/>

## Things to know about containers and blobs

- All blobs must be in a container
- A container can store an unlimited amount of blobs
- Azure storage account can contain an unlimited number of containers
- Create the container in the Azure portal
- You upload blobs in a container
- Use data migration in the Storage Account options to migrate data  
    <br/>

## Configure a Container

- You configure only two things when you create a Blob container:
    - Name:
        - Can only contain lowercase letters, numbers, and hyphens
        - Name must begin with a letter or number
        - Minimum length is three characters
        - Max length is 63 characters
    - Public access level:
        - Access level specifies whether the container and its blobs can be accessed publicly. By default, container data is private and visible only to the account owner. There are three access level choices:
            - **Private(default)** - Prohibit anonymous access to the container and blobs
            - **Blob** - Allow anonymous public read access for the blobs only
            - **Container** - Allow anonymous public read and list access to the entire container, including the blobs
- NOTE: You can also create a blob container with PowerShell by using the `New-AzStorageContainer` command  
    <br/>

## Assign blob access tiers

- Azure Storage supports several access tiers:
    - **Hot Tier:**
        - This is optimized for frequent reads and writes of objects in the Azure Storage account. This is the default tier for new storage accounts. Lowest access cost, but higher storage costs than the Cool and Archive tiers
    - **Cool Tier:**
        - Optimized for storing large amounts of data that is infrequently accessed. Intended for data that remains in the cool tier for at least 30 days. Useful for short-term backup and disaster recovery datasets and older media content. Should not be viewed frequently, but needs to be immediately available. More cost effective to store, but more expensive to access than Hot Tier.
    - **Cold Tier:**
        - Optimized for storing large amounts of data that is infrequently accessed. This tier is intended for data that can remain in the tier for at least 90 days.
    - **Archive Tier**:
        - Offline tier that is optimized for data that can tolerate several hours of retrieval latency. Data must remain in the archive tier for at least 180 days or be subject to an early deletion charge. This includes secondary backups, original raw data, and legally required compliance info. THE MOST COST-EFFECTIVE option for storing data. Accessing data is MORE EXPENSIVE in the Archive tier than accessing data in the other tiers.  
            <br/><br/>![Screenshot 2024-04-10 213738.png](./_resources/Screenshot%202024-04-10%20213738.png)  
            <br/>
- You can change the blob access tier for your account at any time  
    <br/>

## Blob lifecycle management rules

- You can use lifecycle management policy rules to:
    - Transition blobs to a cooler storage tier (Hot to cool, Hot to Archive, Cool to Archive) to optimize for performance and cost.
    - Delete blobs at the end of their lifecycles
    - Define rule-based conditions to run once per day at the Azure storage account level
    - Apply rule-based conditions to containers or a subnet of blobs  
        <br/>

## Blob Types

- Characteristics of different blob types:
    - **Block blobs** - Consists of blocks of data that are assembled to make a blob. Most Blob Storage scenarios use block blobs. Ideal for storing text and binary data in the cloud like files, images, and videos.
    - **Append blob** - Similar to block blob because it consists of blocks of data as well. The blocks data in this are optimized for append operations. Useful for logging scenarios where the amount of data can increase as the logging operation continues
    - **Page blobs** - Can be up to 8tb in size. More efficient for frequent read/write operations. AZ VMs use page blobs for OS disks and data disks
    - Block bob is the default type for a new blob.
    - After you create a blob, you **CANNOT** change its type  
        <br/>

## Knowledge check

- Blob object replication **DOES** require versioning to be enabled