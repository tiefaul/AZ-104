# AZ-104 Notes

## Azure Cloud Shell features

- Is temporary and requires a new or existing Azure Files share to be mounted
- Offers an integrated text editor based on the open-source Monaco Editor
- Authenticates automatically for instant access to your resources
- Runs on a temporary host provided on a per-session, per-user basis
- Times out after 20 minutes without interactive activity
- Requires a resource group, storage account, and Azure File share
- Uses the same Azure file share for both Bash and Powershell
- Is assigned to one machine per user account
- Persists $HOME using a 5-GB image held in your file share
- Permissions are set as a regular Linux user in Bash  
    <br/>

## Use Azure Powershell

- You have two modes for Azure Powershell:
    - **Interactive mode:**
        - You manually issue one command at a time
    - **Scripting mode:**
        - You execute a script that consists of multiple commands  
            <br/>

# Azure Commands (Powershell)

## How to create a resource group using Powershell:

- `$location = (Get-AzResourceGroup -Name az104-03b-rg1).Location` - This is setting a variable for the location to whatever location the resource group listed in `-Name` is
- `$rgName = 'az104-03c-rg1'` - This variable is creating a name for the resource group
- `New-AzResourceGroup -Name $rgName -Location $location` - This creates the resource group  
    <br/>

## How to retrieve the properties of a resource group:

- `Get-AzResourceGroup -Name resourcegroupname`  
    <br/>

## How to create a Manage Disk:

- `$diskConfig = New-AzDiskConfig` - you are defining what is in the New-AzDiskConfig
- `-Location $location` - define property
- `-CreateOption Empty` - define property
- `-DiskSizeGB 32` - define property
- `-Sku Standard_LRS` - define property
- `$diskName = 'namedisk'` - Setting a variable for the disk name
- `New-AzDisk` - Creating the new disk command
- `-ResourceGroupName $rgName` - Using the variable made for the resource group
- `-DiskName $diskName` - Using the variable made for the disk name
- `-Disk $diskConfig` - Using the variable for the disk config  
    <br/>

## Command for retrieving properties for made disk

- `-GetAzDisk -ResourceGroupName $rgName -Name $diskName`  
    <br/>

## Command to increase the memory on the disk

- `New-AzDiskUpdateConfig -DiskSizeGB 64 | Update-AzDisk -ResourceGroupName $rgName -DiskName $diskName`  
    <br/>

## Command to verify memory change has taken affect

- `Get-AzDisk -ResoureGroupName $rgName -Name $diskName`  
    <br/>

## How to verify the current SKU

- `(Get-AzDisk -ResourceGroupName $rgName -Name $diskName).Sku`  
    <br/>

## How to change the SKU

- `NewAzDiskUpdateConfig -Sku Premium_LRS | Update-AzDisk -ResourceGroupName $rgName -DiskName $diskName`  
    <br/>

## How to verify SKU change

- `(Get-AzDisk -ResourceGroupName $rgName -Name $diskName).Sku`  
    <br/>

# Azure Commands (Bash)

## Creating a resource group and an Azure managed disk using Azure CLI (Bash)

- `LOCATION = $(az group show --name 'az104-03c-rg1' --query location --out tsv)` - Creating a variable (LOCATION) to set the region of the resource group.  
    <br/><br/>**NOTE:** I am using the resource group I created before as a reference on where to set the location.  
    <br/>
- `RGNAME = 'az104-03d-rg1'` - Creating a variable (RGNAME) to name the resource group
- `az group create --name $RGNAME --location $LOCATION` - Command to create the resource group  
    <br/>

## Command to retrieve the properties of resource groups

`az group show --name $RGNAME`  
<br/>

## Command to create a new managed disk

- `DISKNAME = 'namedisk2'` - Making a variable for the disk name
- `az disk create \` - Command to create a disk (start of multi-line syntax)
- `--resource-group $RGNAME \` - what resource group to put it in using the RG variable
- `--name $DISKNAME \` - using variable for the name
- `--sku 'Standard_LRS' \` - setting the sku properties
- `--size-gb 32` - Creating the disk size  
    <br/><br/>**NOTE**: When using a multi-line syntax, ensure that each line ends with `\` with no trailing spaces and that there are no leading spaces at the beginning of each line  
    <br/>

## Command to retrieve the properties of the newly created disk

- `az disk show --resource-group $RGNAME --name $DISKNAME`  
    <br/>

## Command to increase disk size

- `az disk update --resource-group $RGNAME --name $DISKNAME --size-gb 64`  
    <br/>

## Verify that disk size was increased

- `az disk show --resource-group $RGNAME --name $DISKNAME --query diskSizeGb`  
    <br/>

## Command to change the disk performance SKU

- `az disk update --resource-group $RGNAME --name $DISKNAME --sku 'Premium_LRS'`  
    <br/>

## Command to verify SKU change

- `az disk show --resource-group $RGNAME --name $DISKNAME --query sku`