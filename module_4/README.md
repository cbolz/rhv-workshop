# Module 4: Storage

Total time: 50 minutes

* What is a storage domain?
* Types of storage domains
* What is the master domain?
* Block vs file protocols
  * Implementation differences (e.g. block = LVM)
  * Limits
* Types of storage
  * iSCSI/FC
  * NFS
  * Gluster
  * Local
* SPM
  
  The Storage Pool Manager (SPM) role is assigned to a single host per data center.  This host is responsible for making metadata changes for all storage domains in the data center.  This includes:
  
  * Create, delete, modify (e.g. expand) virtual disks
  * Create, revert, delete snapshots
  * Template disk management and operations
  
  Any host in the data center may hold the SPM role, RHV-M will ensure that the role is always actve should the host become unavaialble for any reason.
  
* Disk formats
  * qcow2
  * raw
* Storage migration

## Lab: Create a storage domain

Time: 5 minutes

1. Create a new storage domain, using the following information:
   
   * Type: NFS
   * Function: Data
   * Name: workshop
   * Export path: $NFS_HOST:$PATH

## Lab: Upload an ISO

Time: 5 minutes

1. Select the `Upload -> Start` option from the Disks page.
   
1. Choose the $RHEL7_CLOUD image
   
1. Click ok

## Lab: Migrate a disk from one domain to another

Time: 10 minutes

1. From the Disks page, right click $VM_DISK
   
1. Select the "Move" option
   
1. Choose the target storage domain
   
1. Click OK
   
1. The disk will be locked while transferring.  When complete, observe the new location

## Lab: Destroy a storage domain

Time: 10 minutes

1. From the Storage -> Domains page, select $DOMAIN to view the details
   
1. Verify from the Templates tab that no templates use this domain
   
1. Verify from the Disks tab that no devices are hosted in the domain
   
1. Verify from the Leases tab that no leases are using the domain
   
1. From the Data Center tab, highlight $DATACENTER and click the "Maintenance" button
   
1. Once complete, choose the "Detach" option

[Previous](../module_3/README.md) / [Home](../README.md) / [Next](../module_5/README.md)