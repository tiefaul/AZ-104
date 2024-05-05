# AZ-104 Notes

## Options for backing up VMs

Four options for backing up your VMs are:

- **Azure Backup:**
    - This takes a screenshot of your VM and stores the data as recovery points in geo-redundant recovery vaults.
- **Azure Site Recovery:**
    - Protects your VM from a major disaster scenario where a while region experiences an outage due to a major natural disaster or widespread service interruption
- **Azure managed disks-snapshot:**
    - This is a read-only full copy of your VMs HD. Each snapshot is billed based on the actual size used. If you snapshot a disk that's capacity is 64gb but only used 10gb, then you are billed for 10gb
- Azure Managed disks-image:
    - Creates a image that contains all managed disks associate with a VM, including both the OS and data disks  
        <br/>

## Steps to back up your VMs

1.  Create a Recovery Service Vault
2.  Define your backup policy options
3.  Back up your VM  
    <br/>

- You can trigger a backup from one to five times per day
- To run VM backup jobs you need the extension called Microsoft Azure Virtual Machine Agent to be present on the VM (This is different from MARS)  
    <br/>

## Things to know about Soft Delete for backups

- **Soft delete** for VMs only protects deleted backups. If a VM is deleted without a backup, the soft delete feature won't preserve data.
- **Stop backup job**: Before you can delete or retain backup data for your VM, you must stop the active backup job. After you stop the backup job you can choose to delete or retain your backup  
    <br/>

## Azure Site Recovery

- A system where your workloads (like databases, webservers, VPNs, etc) are on one region and then replicated on another region. So if one region goes down, then the other region spins up
- In Azure Site Recovery, the **Azure Traffic Manager** is responsible for connecting the two regions together
- Can also use Site Recovery to replicate on-prem VMware VMs, Hyper-V VMs, physical servers (Windows and Linux) and Azure Stack virtual machines to Azure
- Replicate AWS Windows instances to Azure
- Replicate on-prem VMware VM, Hyper-V VMs managed by System Center VMM, and physical servers to a secondary site
- You can manage replication, failover, and failback from Site Recovery