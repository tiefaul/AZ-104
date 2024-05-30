# Create a blob container client to connect to the storage account on Azure
`BlobContainerClient container = new BlobContainerClient( "ConnectionString", "Container" );`

# Retrieve the blob you want to create a SAS token for and create a BlobClient
```
foreach (BlobItem blobItem in container.GetBlobs())
{
    BlobClient blob = container.GetBlobClient(blobItem.Name);
}
```

# Create a BlobSasBuilder object for the blob you use to generate the SAS token
```
BlobSasBuilder sas = new BlobSasBuilder
{
    BlobContainerName = blob.BlobContainerName,
    BlobName = blob.Name,
    Resource = "b",
    ExpiresOn = DateTimeOffset.UtcNow.AddMinutes(1)
};

// Allow read access
sas.SetPermissions(BlobSasPermissions.Read);
```

# Authenticate a call to the ToSasQueryParameters method of the BlobSasBuilder object
```
StorageSharedKeyCredential storageSharedKeyCredential = new StorageSharedKeyCredential( "AccountName", "AccountKey");

sasToken = sas.ToSasQueryParameters(storageSharedKeyCredential).ToString();
```