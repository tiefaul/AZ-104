# Create route table
   ```
az network route-table create \
        --name <route table name> \
        --resource-group "[resource group name]" \
        --disable-bgp-route-propagation false
```

# Creating a route in the route table
   ```
az network route-table route create \
        --route-table-name <name of route table> \
        --resource-group "[resource group name]" \
        --name <route name> \
        --address-prefix 10.0.1.0/24 \
        --next-hop-type VirtualAppliance \
        --next-hop-ip-address 10.0.2.4
```