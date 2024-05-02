# AZ-104 Notes

## Azure Backup

- Offers a simple solution to back up on-prem resources to the cloud
- Provides isolated backups to guard against accidental deletion of data
- These backups are stored in a **Azure Recovery Services vault** with built in management of recovery points. Can restore when needed
- Outbound data refers to data transferred from a Recovery Service vault during a restore
- Can allow data encryption for secure transmission and storage of data. You store the encryption passphrase locally. Passphrase is never stored in Azure
- Use **Azure Recovery Service vaults** for short-term or long-term data retention. There is no limit to the length in time that data can remain.
- Azure Backup has a limit of 9,999 recovery points per protected instance
- Azure Backup has no cost for implementing on-prem storage devices. It automatically allocates and manages backup storage. Uses a pay-as-you-use model.
- There are multiple storage options **LRS (locally redundant storage)** and **GRS (geo-redundant storage):**
    - *LRS* replicates your data three times (copies it three times) in a storage scale unit in a datacenter. All copies of the data exist within the same region. LRS is a low-cost option for protecting your data from local hardware failures
    - *GRS* is the recommended option. It replicates your data to a secondary region. GRS costs more than LRS, but provides a higher level of reliability for your data.  
        <br/>

## Backup Center

- Azure Backup has a Dashboard (**Backup Center**) where you can monitor, govern, operate, and analyze backups at scale
- Can manage backups spanning multiple workload types, vaults, subscriptions, regions, and tenants
- Uses Azure Policy experience to help you govern backups
- Uses Azure Workbooks and Azure Monitor Logs to help view detailed reports on backups
- Supported in many scenarios:
    - Azure Virtual Machines backup, including SQL and SAP HANA in Azure Virtual Machines backup
    - Azure Files backup, Azure Blob Storage backup, and Azure-managed disks backup
    - Azure Database for PostgreSQL Server backup  
        <br/>

## Recovery Service Vaults

- Makes is easy to backup data, while minimizing management overhead
- Can be used to backup Azure files file shares or on-prem files and folders
- Store backup data for various Azure services, such as IaaS virtual machines and Azure SQL in Azure VMs
- Supports System Center Data Protection Manager, Windows Server, Azure Backup Server, and other services.
- Can create these vaults from the Backup Center dashboard  
    <br/>

## Replication types and when to use them

- Use GRS when Azure is your primary backup storage endpoint
- Use LRS if Azure isn't your primary backup storage endpoint, use LRS to reduce your storage costs
- If you require data availability without downtime in a region and need to guarantee data residency, use ZRS  
    <br/>

## Microsoft Azure Recovery Services (MARS) Agent

- Used to backup files, folders, system data from your on-prem machines and Azure VMs
- This agent must be installed on your Windows client or Windows Server
- The data that is available for backup depends on where you install and run the agent
- Agent does not require a separate backup server
- Is not application-aware. You can restore files and folders from backups, or do a volume-level restore
- Ways to run MARS agent:
    - Run it on-prem to backup your machine data directly to a Recovery Services vault in Azure
    - Run it on VM to backup specific files and folders on your VM. Your Azure VM must run Windows side-by-side with the Azure VM Backup extension
    - Run it on a Microsoft Azure Backup Server (MABS) or a System Center Data Protection Manager (DPM) server. Back up machines and workloads to MABS or DPM by using the MARS agent to backup to a Recovery Service Vault in Azure  
        <br/>

## Steps to configure file and folder backups

1.  Create a Recovery Service vault
2.  Download the MARS agent and credentials file
3.  Install and register MARS agent
4.  Configure Backups