# Create a storage account
```
az storage account create \
                --resource-group <rg name> \
				--access-tier hot \ #(optional)
                --name <name storage account>$RANDOM \ # $RANDOM adds random numbers to the end of the name to make it unique
                --sku Standard_LRS \
                --query "name" | tr -d '"' # (optional) This part uses the tr command to delete (i.e., remove) double-quote characters from the output.
```

<br/>

# Create a container under the storage account
```
az storage container create \
    --name <name of container> \
    --account-name <name of storage account> \
    --public-access off
```

<br/>

# Store your storage account key in a variable
```
STORAGEKEY=$(az storage account keys list \
                --resource-group <rg name> \
                --account-name <storage account name> \
                --query "[0].value" | tr -d '"')
```
