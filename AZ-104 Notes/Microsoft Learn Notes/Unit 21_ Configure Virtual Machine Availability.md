# AZ-104 Notes

## Maintenance Planning

- An **unplanned maintenance** occurs when Azure predicts that the hardware or any platform component associated to a physical machine is about to fail.
- **Unexpected downtime** happens when the hardware of physical infrastructure for you VM fails out of the blue.  
    <br/>

## Availability Sets

- Availability sets are a group of related VMs that are deployed together
- Helps to prevent a single point of failure
- All VMs in these sets should perform the identical set of functions
- Azure ensures the sets run across multiple physical servers, compute racks, storage units, and network switches
- You can create a VM and a availability set at the same time
- To change the availability set for a VM you need to delete and then recreate the VM
- Use Azure portal, Azure Resource Manager Templates (ARM templates), scripting, or API tools to create sets  
    <br/>

## Fault and update domains

- Availability Sets implement a two node concept to help maintain high availability and fault tolerance and each VM is placed in one update domain and one fault domain.
    - Update domain:
        - a group of nodes that are upgraded together during a service upgrade (or rollout)
        - each domain contains a set of VMs and associated physical hardware that can be updated and rebooted at the same time
        - during maintenance, only one update domain is rebooted at a time
        - by default there are only 5 update domains (non-user-configurable)
        - you can configure up to 20 update domains
    - Fault domain:
        - Think of fault domains as nodes that belong to the same rack
        - defines a group of VMs that share a common set of hardware (or switches) that share a single point of failure.
        - 2 fault domains work together to mitigate against hardware failures, network outages, power interruptions, or software updates  
            <br/><br/>![Screenshot 2024-04-21 115516.png](../_resources/Screenshot%202024-04-21%20115516.png)  
            <br/>

## Availability Zones

- A high-availability offering that protects your things from datacenter failures.
- Its a combo of a fault and update domain
- They are unique physical locations within an Azure region
- Each zone has one or more datacenters that are equipped with independent power, cooling, and networking
- To ensure resiliency, there are a minimum of three separate zones within a Azure region
- Zone-redundant services replicate your applications and data across availability zones to protect against single-points-of-failure  
    <br/>

## Vertical and Horizontal scaling

- Vertical scaling:
    - increase or decrease the virtual machine size in response to a workload.
        - increasing disk space, memory, cpu, etc
- Horizontal scaling:
    - used to adjust the number of VMs in your configuration to support the changing workload
    - you either scale out (increase) or scale in (decrease) in the number of VM instances
    - Think of it as creating a whole new server rack to help with your current one
    - Horizontal scaling is more flexible than vertical
  	<br/>
	
  ## Virtual Machine Scale Sets
  
  - Automatically increases the number of your VMs as application demand increases, and reduces the number of machines instances as demand decreases
  - You do not need to pre-provision your VMs
  - As workloads increase, more VM instances are added
  - As workload decrease, VM instances are removed
  - Can be manual, automated, or a combo of both
  - All VM instances are created from the same base OS image and config
  - Supports Azure Load Balancer for basic layer-4 traffic distribution, and Azure Application Gateway for more advanced layer-7 traffic distribution and ssl termination
  - Virtual machine scale set supports up to 1,000 VM instances. If you create and upload your own custom VM image, the limit is 600 instances