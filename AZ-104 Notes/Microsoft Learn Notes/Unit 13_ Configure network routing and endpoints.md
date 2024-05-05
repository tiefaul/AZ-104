# AZ-104

## Review System Routes

- Azure uses *system routes* to direct network traffic between VMs, on prem networks, and the internet. Info about the system routes is recorded in a *route table*
- Azure uses system routes to control traffic for VMs in several ways:
    - Traffic between virtual machines in the same subnet
    - Traffic between VMs in different subnets in the same virtual network
    - Traffic from VMs to the internet
- A route table contains a set of rules (called routes) that specify how packets should be routed in a virtual network
- Route tables record information about the system routes, where the tables are associated to subnets
- Each packet leaving a subnet is handled based on the associated route table
- Packets are matched to routes by using the destination. The destination can be an IP address, a virtual network gateway, a virtual appliance, or the internet
- When a matching route cannot be found, the packet is dropped  
    <br/>

## Identify User-Defined Routes

- Azure automatically handles all network traffic routing, but in some cases, a custom configuration is preferable. In these situation, you can configure user-defined routes (UDRs) and *next hop* targets
- Some characteristics of UDRs:
    - They control network traffic by defining routes that specify the *next hop* of the traffic flow
    - The next hop can be
        - A Virtual network gateway (virtual router)
        - Virtual network
        - Internet
        - Network virtual appliance (NVA)
    - UDRs also access route tables
    - Each route table can be associated to multiple subnets
    - Each subnet can be associated to one route table only
    - There are no charges for creating route tables in Microsoft Azure  
        <br/>

## Determine service endpoint uses

- After *service endpoints* are enabled in your virtual network, you can secure Azure service resources to your virtual network by adding a *virtual network rule* to the resource
- Things to know about service endpoints:
    - They can extend your virtual network identity to your Azure services to secure your service resources.
    - You secure your Azure service resource to your virtual network by using virtual network rules
    - Virtual network rules can remove public internet access to resources, and allow traffic only from your virtual network
    - Service endpoints always take services traffic directly from your virtual network to the services on the Microsoft Azure backbone network
    - Service endpoints are configured through the subnet. No extra overhead is required to maintain the endpoints  
        <br/>

## Things to consider about Service Endpoints

- They improve security when enabled on a virtual network by using virtual network rules. These rules fully remove public internet access to resources, and allowing traffic only from your virtual network.
- Routes in your virtual network the force internet traffic also typically force Azure service traffic to take the same route as the internet traffic. This is called *forced-tunneling*. Service endpoints provide optimal routing for Azure service traffic to allow you to circumvent forced tunneling.
- **NOTE** - With service endpoints, the VM IP addresses switch from public to private IPV4 addresses. Existing Azure service firewall rules that use Azure public IP addresses stop working after the switch. Ensure Azure service firewall rules allow for this switch before you set up service endpoints. You might also experience temporary interruption to service traffic from this subnet while configuring service endpoints  
    <br/>

## Determine Service endpoint services

- In the Azure portal, you select the Azure service for which you want to create the endpoint, it is in a job down menu.

![Screenshot 2024-04-06 143534.png](./_resources/Screenshot%202024-04-06%20143534.png)

## Azure Private Link

- Azure private link provides private connectivity from a virtual network to Azure PaaS, customer owned, or Microsoft partner services.
- Some characteristics are:
    - It keeps all traffic on the Microsoft global network. There is no public internet access
    - Private link is global and there are no regional restrictions. You can connect privately to services running in other Azure regions
    - Services delivered on Azure can be brought into your private virtual network by mapping your network to a private endpoint
    - Private Link can privately deliver your own services in your customer's virtual networks
    - All traffic to the service can be routed through the private endpoint. No gateways, NAT devices, Azure ExpressRoute or VPN connections, or public IP addresses are required  
        <br/>

## Knowledge Check

- Virtual network endpoints extend the private address space in Azure. Endpoints restrict the flow of traffic. As service endpoints are created, Azure creates routes in the route table to direct the traffic