# Creating the VM
```
wget -N https://raw.githubusercontent.com/MicrosoftDocs/mslearn-secure-and-isolate-with-nsg-and-service-endpoints/master/cloud-init.yml && \ # (optional) this is a custom file that will force the vm to update and install apache
az vm create \
    --resource-group <name of rg> \
		--no-wait \ # This is similar to using "docker compose up -d"  
    --name <name of vm> \
		--location <location to deploy> \
    --vnet-name <name of vnet you want vm to be in> \ # (optional) if you have a vnet
    --subnet <name of subnet in the vnet you want the vm to be in> \ # (optional) if you have a subnet in the vnet
    --nsg <name of nsg you want the vm to be in> \ (optional) if you have a nsg or use --asg for asg
    --image Ubuntu2204 \
    --size Standard_DS1_v2 \ # size of disk
     --generate-ssh-keys \
    --admin-username <admin username> \
    --custom-data cloud-init.yml \ # (optional) the wget file from above
    --no-wait \
    --admin-password <password>
```
# List out the VMs you created
```
az vm list \
    --resource-group <rg name> \
    --show-details \
    --query "[*].{Name:name, Provisioned:provisioningState, Power:powerState}" \ # (optional)
    --output table
```
# Creating the variable
```
APPSERVERIP="$(az vm list-ip-addresses \
                 --resource-group <rg name> \
                 --name <name of vm> \
                 --query "[].virtualMachine.network.publicIpAddresses[*].ipAddress" \
                 --output tsv)" # tsv makes the output plain text
```