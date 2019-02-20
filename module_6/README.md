# Module 6: Compute clusters

Total time: 60 minutes

## Cluster settings

* CPU type
* Default network provider
* Memory and CPU optimization
* Migration policy
* Scheduling policy

### Lab: Create and configure a cluster

Time: 20 minutes

1. First we must create the cluster
      
   1. From the Compute -> Clusters page, click the "New" button
      
   1. Complete the form
      
      * General
        * Name: $CLUSTER
        * Management Network: ovirtmgmt
      * Optimization
        * Memory optimization: select "For Server Load"
        * CPU Threads: Count Threads as Cores (checked)
        * Memory Balloon: Enable Memory Balloon Optimization (checked)
        * KSM control: Enable KSM (checked)
      * Scheduling Policy
        * Select Policy: evenly_distributed
        * Enable HA Reservation: (checked)
      
      This lab has configured some common defaults, however **it is a good idea to review all of the settings available here and ensure you understand the purpose, even though this lab only addresses a handful.**
      
      Click OK
      
1. In the following steps we will assign networks which will be accessible in the cluster
   
   1. After the cluster has completed creating, click the name of the cluster to view the details.  Select the "Logial Networks" tab
   
   1. Click the "Manage Networks" button.  When the form appears:
   
      * Check the boxes for "Assign All" and "Require All" for the $VM_NETWORK and $MIGRATION_NETWORK
      * Select the radio button for "Migration Network" for $MIGRATION_NETWORK
      
      Click OK

## Nodes

Nodes are the physical servers which provide capacity for hosting and executing virtual machines.  Adding, removing, and managing nodes is a core component of a RHV deployment.

### Lab: Add a node

Time: 5 minutes

1. From the Compute -> Hosts page, select the "New" button
   
1. Complete the form
   
   * Host Cluster: $CLUSTER
   * Name: $HOSTNAME
   * Authentication -> Password: $PASSWORD
   
   Explore other settings, but leave them at the default values.  Click OK

### Lab: Node maintenance and configuration

Time: 15 minutes

1. After the node from the previous step has registered and becomes avaialable in the interface, click the name to view details
   
1. Click the "Management" button, select the "Maintenance" option
   
1. Review what configuration is applied by default to the host.  Click through each tab in the host details to see the configuration
   
1. Configure the logical networks for the host
   
   * Assign the networks as follows:
     * < logical to physical assignments go here >
     * Assign an IP to the migration network
   
1. Remove the host from maintenance by clicking the "Management" button and selecting the "Activate" option

### (optional) Remove a node

Time: 5 minutes

1. View the node details by selecting the node created in the previous step from the Compute -> Hosts page
   
1. Put the node into maintenance by selecting the "Management" button and the "Maintenance" option
   
1. Press the "Remove" button, confirm your action.  The host will be removed

[Previous](../module_5/README.md) / [Home](../README.md) / Next