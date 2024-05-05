# AZ-104 Notes
## Azure Virtual Network Peering
- This lets you connect Vnets in the same or different regions.
- Two types of peering are *regional* and *global*
	- Regional connects Azure virtual networks that exist in the same region
	- Global connects vnets in different regions
- You can create a global peering of vnets in any Azure public cloud region, or in any China cloud region
- Global peering of vnets in different Azure Government cloud regions are not permitted
- After creating a peer between vnetse, they are still managed as separate resources
<br>
## Things to consider when using Azure Vnet peering


![Screenshot 2024-04-04 172112.png](./_resources/Screenshot%202024-04-04%20172112.png)
<br>
## Things to know about vreating virtual network peering
- Your account must be assigned to the Network Contributor or Classic Network Contributor role. 
- Need two vnets
- The second vnets in the peering is referred to as the remote network
- Initially the virtual machines in your vnets cannot communicate with each other. After the peering is estabished, the machines can communicate iwthin the peered netowork based on your config settings
<br>
## How to check your peering status
- Your peering isn't successfully established until both bnets in the peering have a status of connected.
- For deployment iwth the Azure Resource Manager, the two primary status conditions are initiated and connected. For the classic deployment model, the Updating status condition is also used.
- When you create the initial peering to the second (remote) vnet from the first vnet, the peering status for the first virtual network is initiated.
- When you create the subsequent peering from the seconf vnet to the first vnet, the peering status for both the first and remote virtual networks is Connected. In the Azure portal, you can see the status for the first vnet change from initiated to connected.
<br>
## Extend peering with user-defined routes and service chaining
- Suppose you have network A, B, C. You connect A to B and B to C. A and C don't automatically connect because you connected B and C.
## Things to know about extending peering
- Few ways to extend the capabilities of your peering for resources and vnets outside your peering network are:
	- Hub and spoke networks
	- User-defined routes
	- Service chaining
<br>
## Knowledge Check
- **Gateway transit** allows peered vnets to share the gateway and get access to resources