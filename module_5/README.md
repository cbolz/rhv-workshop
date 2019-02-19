# Module 5: Network

Total time: 60 minutes

* Physical interfaces
  
  Each host must have one or more physical interfaces for network connectivity.  These can be configured in many different ways, including using bonding to provide highly avaialble connectivity to the logical networks hosted.
  
* Logical networks
  
  Logical networks are created on top of physical interfaces and represent the VLANs and other networking entities to provide, most commonly, logical isolation.
  
* Network roles
  * Management - Connectivity between the host and RHV-M
  * Storage - Storage domain traffic utilizing IP storage (e.g. iSCSI, NFS)
  * Migration - Live migration traffic falls into this category
  * Virtual machine network(s) - This is the traffic to and from virtual machine network interfaces
  * Display - This traffic type represents the VNC and/or SPICE connections to virtual machine consoles
  
* vNIC profiles
  
  vNIC profiles provide the ability to define important characteristics for network adapaters used by virtual machines:
  
    * QoS policies - customize and specify a QoS policy for a particular VM interface
    * Network filter - the network filters provide host level protection for certain aspects, e.g. preventing MAC spoofing by virtual machines.

## Lab: Create a new VLAN logical network for virtual machines

Time: 15 minutes

It is common for virtual machines to be assigned to different logical networks for many different reasons.  Creating and manaing logical networks using RHV-M is easy and only takes a few minutes to define the network and configure it for the clusters and hosts.

1. First, we define the network.  From the Network -> Networks page, select the "New" button
   
   1. Fill in the fields:
      
      * General:
        * Data Center: $DATACENTER
        * Name: $NAME
        * Enable VLAN tagging: checked; VLAN: $VLAN
        * All other values at default
      * Cluster:
        * $CLUSTER -> Attach all and Reqire all selected
      
   1. Click OK
   
1. Next, configure the network on the hosts.  From the Compute -> Hosts page, click $HOST to view details
      
   1. Select the Network Interfaces tab, click the "Setup Host Networks" button
      
   1. Drag and drop the network to the $INTERFACE interface
      
   1. Click OK
      
   1. (optional) Repeat for other hosts in the cluster

## Lab: Create a new VLAN logical network for migration traffic

Time: 20 minutes

This lab will create a dedicated migration network for the hosts to utilize.  A dedicated network allows the assignment of a QoS policy to prevent migration traffic from saturating the physical resources, while also enhancing the security posture by providing an isolated network for the unencrypted migration traffic.

The same process can be followed for other network traffic types, e.g. dedicated iSCSI and/or NFS networks.

1. First, we will need to create a QoS policy to limit the amount of throughput migration traffic is allowed to consume.  From the Compute -> Data Centers page, select $DATACENTER to view details
   
   1. Select the "QoS" tab, scroll down to the "Host Network" section.  Click the button for "New"
      
   1. Complete the form:
      
      * QoS Name: Migration_Traffic_Limit
      * Weighted Share: 10
        
        Note that the value here is from 1-100, with higher representing more share during contention.  If migration traffic is a low priority, you may consider setting higher weighted shares for virtual machine, storage, or other traffic types.  This value is relative to other weighted share values for networks sharing the physical interface, so a value of 100 here will not cause this QoS policy to dominate the interface all of the time.
      
      * Rate Limit: 250
      * Committed Rate: 1
      
      Click OK
      
1. Next, we will need to define the network.  From the Network -> Networks page, select the "New" button
      
   1. Fill in the fields:
      
      * General:
        * Data Center: $DATACENTER
        * Name: $NAME
        * Enable VLAN tagging: checked; VLAN: $VLAN
        * Uncheck the "VM network" box
        * Host Network QoS: Migration_Traffic_Limit
        * All other values at default
      * Cluster:
        * $CLUSTER -> Attach all and Reqire all selected
      
      Click OK
      
   1. Once the network is created and listed on the Network -> Networks page, click the name to view details
   
   1. Select the Clusters tab, observe the "Network Role" column.  Click the "Manage Network" button
   
   1. For $CLUSTER, check the box for "Migration Network".  Click OK
   
1. Last, we will configure the network on the hosts.  From the Compute -> Hosts page, select $HOST to view details
   
   1. Select the "Network Interfaces" tab.  Click the "Setup Host Networks" button
      
   1. Drag and drop the network with title $NAME from the right side to interface $INTERFACE.  Click the pencil in the corner of the network box to edit the properties.
      
   1. Complete the form:
      
      * IPv4
        * Boot protocol: Static
        * IP: $IP_ADDRESS
        * Netmask: $NETMASK
        * Gateway: (empty)
      * All other fields at default
      
      Click OK
      
   1. (optional) Repeat for other hosts in the cluster

## Lab: Create a vNIC profile

Time: 10 minutes

1. From the Network -> vNIC Profiles page, select the "New" button
   
1. Complete the form:
   
   * Data Center: $DATACENTER
   * Network: $VM_NETWORK
   * Name: $VM_NETWORK_nofilter
   * Network Filter: No Network Filter
   * All other fields at default
   
   Press OK
   
1. From the Compute -> Virtual Machines page, right click $VIRTUAL_MACHINE, select the "Edit" option
   
   Add a NIC to the virtual machine using the newly defined vNIC profile.

[Previous](../module_4/README.md) / [Home](../README.md) / [Next](../module_6/README.md)