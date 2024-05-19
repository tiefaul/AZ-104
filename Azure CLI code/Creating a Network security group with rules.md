# Creating a NSG
```
az network nsg create \
    --resource-group <rg name> \
    --name <name the nsg>
```

# Creating a HTTP rule for NSG
```
# This creates a nsg rule to deny port 80(http) traffic to a specific VM
az network nsg rule create \
    --resource-group <name of resource group> \
    --nsg-name <name of nsg> \
    --name httpRule \
    --direction Inbound \
    --priority 150 \
    --source-address-prefixes 10.0.1.4 \ # VM (DataServer) requesting the port 80 connection
    --source-port-ranges '*' \
    --destination-address-prefixes 10.0.0.4 \ # The receiving VM (AppServer) for port 80 connection
    --destination-port-ranges 80 \ # http port
    --access Deny \
    --protocol Tcp \
    --description "Deny from DataServer to AppServer on port 80"
```

# Creating a SSH rule for NSG to allow VMs within the NSG to be SSH into
```
az network nsg rule create \
    --resource-group <name of rg> \
    --nsg-name <name of the nsg> \
    --name AllowSSHRule \
    --direction Inbound \
    --priority 100 \ # The lower the priority = higher the presidence
    --source-address-prefixes '*' \ # Allows anyone to attempt to connect to the destination
    --source-port-ranges '*' \
    --destination-address-prefixes '*' \ # All the VMs within the NSG
    --destination-port-ranges 22 \ # Port for SSH
    --access Allow \
    --protocol Tcp \
    --description "Allow inbound SSH"
```

