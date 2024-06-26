# Create the VNet 
```
az network vnet create \
    --resource-group <rg name> \
    --name <name vnet> \
    --address-prefixes 10.0.0.0/16 \
    --subnet-name Applications \ (Optional) do this if you want to go ahead and add a subnet in the VNet
    --subnet-prefixes 10.0.0.0/24
```
# Creating a subnet for a VNet
```
az network vnet subnet create \
    --resource-group <rg name> \
    --vnet-name <name of vnet> \
    --address-prefixes 10.0.1.0/24 \
    --name Databases
```
# How to list out VNets
`az network vnet list --query "[?contains(provisioningState, 'Succeeded')]" --output table`
# How to associate a subnet with a NSG
```
az network vnet subnet update \
		--vnet-name <name> \
		--name <subnet name> \
		--resource-group <rg name> \
		--network-security-group <NSG name> \
```