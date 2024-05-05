# AZ-104 Notes

## Things to know about Azure Load Balancer

- Can be used for inbound and outbound traffic
- Can implement a public or internal balancer
- To implement a load balancer, you configure four components:
    - Front-end IP configuration
    - Back-end pools
    - Health probes
    - Load-balancing rules
- The front-end config specifies the public or internal IP that your load balancer responds to
- The back-end pools are your services and resources, including Azure VMs or instances in Azure Virtual Machine Scale Sets
- Load-balancing rules determine how traffic is distributed to back-end resources
- Health probes ensure the resources in the backend are healthy
- Load Balancer scales up to millions of TCP and UDP application flows
- Admins use public load balancers to map public IP addresses and ports of incoming traffic to private IP addresses and ports of VMs  
    <br/>

## Implement an Internal Load Balancer

- Admins use internal load balancers to direct traffic to resources that reside in a virtual network, or to resources that use a VPN to access Azure infrastructure  
    <br/>

## Determine load balancer SKUs

- Azure load balancer supports three SKUs:
    - Basic
    - Standard
    - Gateway
- Each provide different features, scenario scaling, and pricing
- New designs and architectures should use the Standard SKU
- The Gateway SKU supports high performance and high availability scenarios with third-party network virtual appliances (NVA)  
    <br/>

## Comparing Basic and Standard SKU features

![Screenshot 2024-04-07 161729.png](./_resources/Screenshot%202024-04-07%20161729.png)  
<br/>

## Back-end Pools

- Each load balancer has one or more back-end pools that are used for distributing traffic. These pools contain IPs of the virtual NICs that are connected to your load balancer.
- Basic SKU allows up to 300 pools, the Standard SKU allows up to 1,000
- When configuring back-end pools, you can connect to availability sets, VMs, or Azure Virtual Machine Scale Sets
- Basic SKU can select VMs in a single availability set or VMs in an instance of Azure Virtual Machine Scale Sets
- Standard SKU can select VMs or Virtual Machine Scale Sets in a single virtual network. Your config can include a combination of VMs, availability sets, and VM scale sets
- NOTE: Think of pools as a set of web servers (that you configure) that the load balancer sends traffic to  
    <br/>

## Health Probes

- A probe allows your load balancer to monitor the status of a application. It can dynamically add or remove VMs from your load balancer rotation based on machine response to health checks. When a probe fails to response, the load balancer stops sending connections to unhealthy VMs
- Two main ways to configure a custom health probe:
    - HTTP
    - TCP
- In a HTTP probe, load balancer probes your back-end pool endpoints every 15 seconds. A VM instance is considered healthy if it responds with an HTTP 200 message within the specified timeout period (default is 31 seconds)
- A TCP probe relies on establishing a successful TCP session to a defined probe port.
- To configure a probe, you specify values for the following settings:
    - **Port**: Back-end port
    - **URI**: URI for requesting health status from the backend
    - **Interval**: Amount of time between probe attempts (default 15 seconds)
    - **Unhealthy** threshold: Number of failures that must occur for the instance to be considered unhealthy  
        <br/>

## Session Persistence

- This specifies how to handle traffic from a client. By default, successive requests from a client go to any virtual machine in your pool
- You can modify the session persistence behavior:
    - **None**(default): Any VM can handle the request
    - **Client IP**: Successive requests from the same client IP address go to the same VM
    - **Client IP and Protocol**: Successive requests from the same client IP address and protocol combination go to the same VM
- NOTE: Maintaining session persistence information is important for applications that implement a shopping cart  
    <br/>

## Knowledge Check

- The default distribution type for traffic through a load balancer is a **five-tuple hash**