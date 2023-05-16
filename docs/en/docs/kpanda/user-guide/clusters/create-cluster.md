---
date: 2022-11-17
hide:
  - toc
---

# Creating a Worker Cluster

In the DCE 5.0 container management module, [cluster roles](./cluster-role.md) are divided into four categories: global service cluster, management cluster, working cluster, and access cluster. An integrated cluster can only be accessed from third-party vendors (see [Integrate-cluster](./integrate-cluster.md)). This page describes how to create a worker cluster.

## Prerequisites

Certain prerequisites must be met before creating a cluster:

- Prepare an adequate number of nodes according to business needs.
- Kubernetes version 1.22+.
- The destination host must allow IPv4 forwarding. If the Pod and Service are using IPv6, the destination server needs to allow IPv6 forwarding.
- For now, DCE does not provide firewall management functionality. You need to pre-define the firewall rules of the target host by yourself. To avoid problems during cluster creation, it is recommended to disable the firewall of the target host.
- See Node Availability Check.

## Steps

1. On the `Cluster List` page, click the `Create Cluster` button.
2. Fill in the basic information of the cluster by referring to the following requirements, and click `Next`.

    - Cluster name: The name should contain only lowercase letters, numbers, and hyphens ("-"). It must start and end with a lowercase letter or number and can be up to 63 characters long.
    - Managed: Choose which cluster will manage the cluster, such as creating, upgrading, node scaling, deleting clusters, etc. during the cluster life cycle.
    - Runtime: Select the runtime environment of the cluster, currently supporting containerd and docker (see How to Choose a Container Runtime).
    - Kubernetes version: Three version spans are supported, depending on the version supported by the managed cluster.
    
3. Fill in the node configuration information and click `Next`.
   
    - High availability: Enable high availability mode for production environments. At least three controller nodes are needed. Only one controller node is provided after shutdown.
    - Authentication method: Choose to access the node through a username/password or public and private key.
    - Use a unified password: After enabling it, the access passwords of all nodes in the cluster are the same, and you need to enter the unified password for accessing all nodes below. If off, individual usernames and passwords can be set for each node.
    - Node Check: Pre-check the connectivity of nodes. This is optional, and the check can be skipped.
    - NTP time synchronization: After it is turned on, the time on each node will be automatically synchronized.
    
4. Fill in the network configuration information and click `Next`.

    - Network plug-in: Responsible for providing network services for Pods in the cluster. The network plug-in cannot be changed after the cluster is created. Supports cilium and calico. Selecting none means that the network plugin will not be temporarily installed.
    - Container network segment: The network segment used by containers in the cluster, which determines the upper limit of the number of containers in the cluster. Cannot be modified after creation.
    - Service network segment: The network segment of Service resources used by containers in the same cluster to access each other, which determines the upper limit of Service resources. Cannot be modified after creation.

5. Fill in the plug-in configuration information and click `Next`.

6. Fill in advanced configuration information and click `OK`.
   
    - `kubelet_max_pods`: Set the maximum number of Pods per node. The default is 110.
    - `hostname_override`: Reset the hostname. It is recommended to use the default value, and use the name generated by the system as the hostname by default.
    - `kubernetes_audit`: Kubernetes audit log, enabled by default.
    - `auto_renew_certificate`: Automatically renew the Kubernetes control plane certificate on the first Monday of each month, enabled by default.
    - `disable_firewalld&ufw`: Disable the firewall to prevent the node from being inaccessible during installation.
    - `Insecure_registries`: Private container registry configuration. When using a private Container registry to create a cluster, fill in the address of the private Container registry here to bypass the certificate authentication of the container engine and obtain the image.
    - `yum_repos`: Fill in the Yum source registry address.

## Complete Creation

After filling in the correct information and completing the above steps, the page will prompt that the cluster is being created.

!!! note

    Creating a cluster takes a long time, so you need to wait patiently. In the meantime, you can click the `Back to Cluster List` button to return to the cluster list page and wait for the cluster creation to complete. To view the current status, click `Real-time Log`.

When the cluster is in an unknown state, it means that the current cluster has been disconnected. The data displayed by the system is the cached data before the disconnection, which does not represent real data. At the same time, any operations performed in the disconnected state will not take effect. Please check the cluster network connectivity or Host Status.