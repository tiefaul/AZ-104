# Creating the variable
```
APPSERVERIP="$(az vm list-ip-addresses \
                 --resource-group <rg name> \
                 --name <name of vm> \
                 --query "[].virtualMachine.network.publicIpAddresses[*].ipAddress" \
                 --output tsv)" # tsv makes the output plain text
```