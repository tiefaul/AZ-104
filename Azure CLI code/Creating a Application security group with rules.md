# Creating a App Security Group
```
az network asg create \
    --resource-group $rg \
    --name ERP-DB-SERVERS-ASG
```
# Associating VM with ASG
```
az network nic ip-config update \
    --resource-group <name of rg> \
    --application-security-groups <name of the asg> \
    --name <name of the VM's IP configuration> \
    --nic-name <name of the NIC on the VM you want to update> \
    --vnet-name <name of the vnet the vms are on> \
    --subnet <name of the subnet they are on within the vnet>
```
# Updating the NSG to add the new ASG 
```
az network nsg rule update \
    --resource-group <name of rg> \
    --nsg-name <nsg name> \
    --name httpRule \
    --direction Inbound \
    --priority 150 \
    --source-address-prefixes "" \ # No need to add because of ASG
    --source-port-ranges '*' \
    --source-asgs <name of asg> \
    --destination-address-prefixes 10.0.0.4 \
    --destination-port-ranges 80 \
    --access Deny \
    --protocol Tcp \
    --description "Deny from DataServer to AppServer on port 80 using application security group"
```

# Notes
- ASG are good for NSGs because you can assign a list of NICs to a ASG and reference them in your NSG