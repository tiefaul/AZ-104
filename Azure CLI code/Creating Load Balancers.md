# Creating a public IP for load balancer
```
az network public-ip create \
  --resource-group [sandbox resource group name] \
  --allocation-method Static \
  --name myPublicIP
```
# Create Load Balancer
```
az network lb create \
  --resource-group [sandbox resource group name] \
  --name myLoadBalancer \
  --public-ip-address myPublicIP \
  --frontend-ip-name myFrontEndPool \
  --backend-pool-name myBackEndPool
```
# Creating a health probe
```
az network lb probe create \
  --resource-group [sandbox resource group name] \
  --lb-name myLoadBalancer \
  --name myHealthProbe \
  --protocol tcp \
  --port 80
# To allow the load balancer to monitor the healthcare portal's status, create a health probe. The health probe dynamically adds or removes virtual machines from the load-balancer rotation based on their response to health checks.
```  
# Creat LB Rule
```
az network lb rule create \
  --resource-group [sandbox resource group name] \
  --lb-name myLoadBalancer \
  --name myHTTPRule \
  --protocol tcp \
  --frontend-port 80 \
  --backend-port 80 \
  --frontend-ip-name myFrontEndPool \
  --backend-pool-name myBackEndPool \
  --probe-name myHealthProbe
# Now, you need a load balancer rule to define how traffic is distributed to the virtual machines. You define the front-end IP configuration for the incoming traffic and the back-end IP pool to receive the traffic, along with the required source and destination port. To make sure only healthy virtual machines receive traffic, you also define the health probe to use.
```
# Connecting VM to the back-end pool by updating their NICs
```
az network nic ip-config update \
  --resource-group [sandbox resource group name] \
  --nic-name webNic1 \
  --name ipconfig1 \
  --lb-name myLoadBalancer \
  --lb-address-pools myBackEndPool
```
# Command to get load balancer public IP
```
echo http://$(az network public-ip show \
                --resource-group [sandbox resource group name] \
                --name myPublicIP \
                --query ipAddress \
                --output tsv)
```
- You can create a internal load balancer the same way you would create a external one
	- When you create the load balancer, select internal for the type
	- Assign a private IP instead of a public IP for the LB front end
	- Then place the LB in the protected VNet that contains the VMs you want to handle the request