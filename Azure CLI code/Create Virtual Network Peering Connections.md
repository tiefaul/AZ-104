# How to create a VNet peer
```
az network vnet peering create \
    --name SalesVNet-To-MarketingVNet \
    --remote-vnet MarketingVNet \ # What you are remoting to
    --resource-group "learn-790b7ffe-44d2-4eef-b9b6-40610aca2029" \
    --vnet-name SalesVNet \ # The one requesting the remote
    --allow-vnet-access
```

- Remember you have to do this to both vnets, so in this instance you would have to reverse the command and make the marketingvnet the one requesting. (Unless you do it through the Azure Portal)
# How to list the VNet peering connections
```
az network vnet peering list \
    --resource-group "learn-790b7ffe-44d2-4eef-b9b6-40610aca2029" \
    --vnet-name SalesVNet \ # The VNet you want to check to see if the peering connection is up
    --query "[].{Name:name, Resource:resourceGroup, PeeringState:peeringState, AllowVnetAccess:allowVirtualNetworkAccess}"\
    --output table
```
# How to check effective routes for a VM in a subnet
```
az network nic show-effective-route-table \
    --resource-group "rg name" \
    --name <name of vm you want to check> \
    --output table
```