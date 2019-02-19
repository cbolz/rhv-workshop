# Module 1: Familiarization and interface overview

Total time: 35 minutes

## The lab environment

This will contain a description of the lab, e.g. number of hosts, clusters, etc. along with credentials and how to access resources.

## RHV concepts

* Datacenter
* Cluster
* Node/host
* Network
* Storage domains
* Virtual machine

## Lab: Explore aspects of the GUI

Time: 20 minutes

1. View and explore the dashboard and familiarize with the navigation of RHV-M
   
   Log in to the admin portal, explore different aspects of the compute, network, storage, and administration tabs
   
   * Where can I find hosts managed by this RHV-M?
   * What hosts are in $CLUSTER?
   * How can I see which VMs are on $HOST?
   * Where do we see the full list of data disk images?
   * How do I see disks for a specific domain?
   
1. Explore RHV-M’s data center and cluster concepts, see which properties are set and what entities are contained in each object type
   
   From the admin portal, browse the Data Centers and Clusters pages.  Click on the objects, see their properties and contents.
   
   * Data Centers - $DATACENTER_NAME
   * Storage Domains - note that they are controlled at the datacenter level.  
   * Logical networks - explore the networks, what purpose do they serve, what properties are changed here (e.g. MTU, VLAN), how are networks assigned to a cluster?
   * Clusters - which clusters belong to the datacenter?
   * QoS - What resources can have QoS policies?  For each of those, what constraints can be put in place?

Previous / [Home](../README.md) / [Next](../module_2/README.md)