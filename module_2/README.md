# Module 2: Virtual machines

Total time: 45 minutes

Virtual machine attributes:
* CPU
* Memory
* Disk
* Network
* Cloud-Init

## Lab: Create a virtual machine

Time: 15 minutes

1. VM parameters:
   
   * 1 vCPU, 2 GB RAM
   * connect to $NETWORK
   * attach an existing rhel cloud disk image
   * create a second 20GB data disk in $STORAGE_DOMAIN
   
1. Use cloud-init to customize the image (e.g. set the password)

## Lab: Start and connect to the virtual machine using the VM portal

Time: 5 minutes

1. Login to the VM portal
   
1. Start the VM
   
1. Connect to the console, see it boot

## Lab: Create, use, and delete a snapshot from the VM portal

Time: 10 minutes

1. From the vm portal, create a snapshot
   
1. Log into the VM, create a file with some data
   
1. Revert the snapshot
   
1. Delete the snapshot

## Lab: Live migration

Time: 5 minutes

1. From the admin portal, manually migrate the virtual machine

[Previous](../module_1/README.md) / [Home](../README.md) / [Next](../module_3/README.md)