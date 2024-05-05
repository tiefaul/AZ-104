# AZ-104 Notes

## Plan Virtual Networks

- Azure network services offer a range of components with functionalities and capabilities, as shown below

![Screenshot 2024-04-01 110314.png](./_resources/Screenshot%202024-04-01%20110314.png)  
<br/>

## Things to know about Azure virtual networks

- An Azure virtual network is a logical isolation of the Azure cloud resources
- You can use virtual networks to provision and manage VPNs in Azure
- Each virtual network has its own Classless Inter-Domain Routing (CIDR) block and can be linked to other virtual networks and on-prem networks
- You can link virtual networks with an on-prem IT infrastructure to create hybrid or cross-premises solutions, when the CIDR blocks of the connecting networks don't overlap
- You control the DNS server settings for virtual networks, and segmentation of the virtual network into subnets  
    <br/>

## Things to know about subnets

- There are certain conditions for the IP addresses in a virtual network when you apply segmentation with subnets
    - Each subnet contains a range of IP addresses that fall within the virtual network address space
    - The address range fora subnet must be unique within the address space for the virtual network
    - The range for one subnet can't overlap with other subnet IP address ranges in the same virtual network
    - The IP address space for a subnet must be specified by using CIDR notation
    - You can segment a virtual network into one ore more subnets in the Azure portal.

## Reserved addresses

- For each subnet, Azure reserves five IP addresses. The first four addresses and the last address are reserved.
- Example of the reserved addresses in the IP range of `192.168.1.0/24`

![Screenshot 2024-04-01 112056.png](./_resources/Screenshot%202024-04-01%20112056.png)  
<br/>