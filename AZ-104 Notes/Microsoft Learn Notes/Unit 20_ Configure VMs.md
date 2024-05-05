# AZ-104 Notes

## VM pricing options

- subscription is billed at two separate costs for every VM:
    - **Compute:**
        - These are priced on a per hour basis, but billed on per minute basis
        - Hourly price varies based on the VM size and OS you select.
        - For compute you are able to choose from two payments options:
            - **Consumption-based:**
                - Able to increase or decrease on demand
                - Use if you run an App with short-term or unpredictable workloads
                - Best example is a quick test or developing an app in a VM
            - **Reserved VM instance (RI):**
                - Commitment is made up front, and in return you get 72% price savings compared to pay-as-you-go
                - Easily be exchanged or returned for an early termination fee
                - Use if VM has to run continuously, or need budget predictability
                - Can only commit to using for at least 3 years
    - **Storage**:
        - Charged separately for Azure Storage used by the VM.
        - Always charged for any Azure Storage used by the disks  
            <br/>

## Virtual Machine storage and disks

- Each VM has at least two disks (They can also have one or more data disks):
    - **OS Disk** - registered as a SATA drive and label `c:` by default
    - **Temp Disk**\- Data here might be lost during a maintenance event or when you redeploy a VM. During a standard reboot, the data on the temp drive should persist. Any data on the temp disk should not be critical to the system.
    - On windows the temp disk is labeled `D:` and used for storing the pagefile.sys file
    - On Linux the temp disk is typically `/dev/sdb`. The disk is formatted and mounted to `/mnt` by the Azure Linux Agent  
        <br/>

## Data Disks

- These are managed disks that attach to a VM to store app data, or other data.
- Registered as SCSI drives and are labeled with a letter you choose.
- Size of the VM determines how many data disks you can attach and the type of storage you can use to host the data disks  
    <br/>

## Things to know when choosing storage

- You can attach several Premium Storage disks to a vm
- Using **Multiple storage disks** gives your applications up to 256TB per VM
- With premium storage, your apps can achieve **80,000 I/O per VM**
- Get a disk throughput of **2,000 MB per second per VM**  
    <br/>

## Azure Bastion

- This is a subset to RDP or SSH except it does not need a the **VMs public IP address**
- You can connect to a VM with the full GUI interface, just like RDP  
    <br/>

## Knowledge Check

- **Memory-Optimized** VMs are better for large in-memory business critical workloads that require massive parallel computer power. Good for database servers, medium to large caches and in-memory analytics
- **Compute-Optimized** VMs are designed to have high CPU-to-memory ratio. Suitable for medium traffic web servers, bath processes, application servers, and **running Network Appliances**

![Screenshot 2024-04-18 194949.png](../_resources/Screenshot%202024-04-18%20194949.png)