---
title: KOP Dashboard - Resource Quotas
description: Official Rafay product documentation. Explore "KOP Dashboard - Resource Quotas" docs and more here. Rafay is a SaaS-first Kubernetes Operations Platform with enterprise-class scalability.
tags:
  - Resource Limits
  - Project Quotas
  - Namespace Allocation
  - Quota Management
  - Resource Utilization
---

A detailed Resources Quotas dashboard is available for every Project to set quotas that are enforced across all the namespaces within a cluster and all the quotas supported by Kubernetes resource quotas are available. A project would have a default quota per namespace within a cluster which would be propagated to the namespace when it's created on the cluster. The default quotas for all the namespaces (in a cluster) in a Project should not exceed the Project quota. The quotas are actively enforced on the cluster using namespace ResourceQuota.

---

## Resources Quotas Access

Perform the below steps to access the Resource Quotas from the controller:

- Login to the console and open the Home page
- Select the required project and click **Settings** gear icon. An illustrative example is shown below by selecting a project **defaultproject**

![Project Dashboard](img/projects/home_page.png)


General Settings page appears by default.

- Click **Resource Quotas** tab to set the namespace quotas
- Click **Configure** for the required resource type
- Provide a **Project Limit** and **Namespace Limit** as shown below

!!! IMPORTANT
    Namespace Limit is mandatory when setting the Project Limit and vice-versa


| Resource Type | Description                          |
| --------------- |------------------------------------- |
| CPU Limit  | 	The maximum amount of CPU (in millicores) allocated to the project/namespace |
| CPU Request  | The minimum amount of CPU (in millicores) guaranteed to the project/namespace|
| Memory Limit  | 	The maximum amount of GPUs allocated to the project/namespace |
| Memory Request  | 	The minimum amount of GPUs guaranteed to the project/namespace |
| GPU Limit  | 	The maximum amount of memory (in bytes) allocated to the project/namespace |
| GPU Request  | 	The minimum amount of memory (in bytes) guaranteed to the project/namespace |
| Storage Request | The minimum amount of storage (in gigabytes) guaranteed to the project/namespace |
| Services Load Balancers  | The maximum number of load balancers services that can exist in the project/namespace|
| Services Node Ports  | 	The maximum number of node port services that can exist in the project/namespace |
| Pods  | 	The maximum number of pods that can exist in the project/namespace in a non-terminal state (i.e., pods with a state of .status.phase in (Failed, Succeeded) equal to true) |
| Services  | 	The maximum number of services that can exist in the project/namespace |
| ConfigMaps | The maximum number of ConfigMaps that can exist in the project/namespace |
| Persistent Volume Claims | The maximum number of persistent volume claims that can exist in the project/namespace|
| Replications Controllers  | 	The maximum number of replication controllers that can exist in the project/namespace |
| Secrets  | 	The maximum number of secrets that can exist in the project/namespace |


!!! IMPORTANT
      Project Limit must always be higher than the Namespace Limit. Configmaps and Secrets are utilized for various purposes internally in the Kubernetes lifecycle, thus configuring low quotas for configmaps or secrets might prevent regular operations (e.g., workload deployments on the clusters). To avoid such blockages, set the project limit to 100 or more for these two resource types


![Project Dashboard](img/projects/resources-quotas.png)

> **Note:** To configure `ephemeralStorageLimits` and `ephemeralStorageRequests`, use [RCTL](./quotas_cli.md), API, or Terraform.


- Click **Save** to set the configuration

Once the quotas are successfully set, these limits are automatically applied to the clusters deployed in that specific project.
Quota validation occurs at the time of namespace publishing. If sufficient quota is available based on cluster resource limits, the namespace publish succeeds; otherwise, it fails.

### Utilizations

Utilizations page shows the quota details used for the resource at the time of namespace creation and remaining quota limit.

- Click **Utilizations**

![Project Dashboard](img/projects/utilization-button.png)

- Utilization page appears with the details on Resource Type, Project Limit, Namespace Limit, and Utilizations

![Project Dashboard](img/projects/utilization_details.png)

- Click **Back to Resource Quota** to view the Resource Quotas page

---

## Quota Overrides

By default, the **Project Resource Quota** applies to all clusters within a project. **Quota overrides** provide flexibility by allowing users to set specific resource limits for individual clusters, rather than relying solely on project-level quotas. This ensures that resources are allocated according to the unique needs of each cluster, enabling more granular control over resource utilization and helping to meet various operational requirements.

>💡 **Important**
> Only Org Admins have the permission to create quota overrides, while Org Read-Only Admins can only view the quota overrides
> Quota Override is supported across various interfaces, including the UI, [CLI](./quotas_cli.md), [API](../../automation/api/apis.md), and [Terraform](https://registry.terraform.io/providers/RafaySystems/rafay/latest/docs/resources/cluster_override)


### Cluster-Specific Quotas via UI

To apply different quotas for individual clusters, users can define overrides using a YAML specification as explained below:  

- Click **New Override**, provide a name, and click **Create**

![Resource Quotas for Namespaces](img/projects/new_quotas.png)

- In the **Placement** section, click the placement type drop-down and select **Specific Clusters**. All clusters available in this project are listed  
- Select one or more clusters
- In the **Override Values** section, upload the YAML file or pull the file from a directory

![Resource Quotas for Namespaces](img/projects/yaml_specs.png)

The following YAML example demonstrates how to override the CPU request quota for a specific cluster within a project

```
apiVersion: system.k8smgmt.io/v3
kind: Project
metadata:
  name: example-project
patch:
- op: replace
  path: /spec/clusterResourceQuota/cpuRequests
  value: 200m
```

__Example Explanation__

- The `metadata` name in the spec must match the project name. In this instance, users can create the cluster quota override using the above spec only in the project **example-project**
- This patch updates the **cpuRequests** field under `clusterResourceQuota` for the project named `example-project`  
- It replaces the existing CPU request value with ```200m (milli cores)```, without modifying the CPU limit
- Only the specified cluster(s) will be affected, while others continue using the default cluster limit configured in project settings  


#### Supported Resource Types

The supported resource types include ```configMaps```, ```cpuLimits```, ```cpuRequests```, ```gpuLimits```, ```gpuRequests```, ```memoryLimits```, ```memoryRequests```, ```persistentVolumeClaims```, ```pods```, ```replicationControllers```, ```secrets```, ```services```, ```servicesLoadBalancers```, ```servicesNodePorts```, and ```storageRequests```.

Overrides must follow the ***lower camel case*** naming convention and use the path format: ```/spec/clusterResourceQuota/<resource_name>```.

>💡 **Important**
> Only the replace operation is supported for cluster quota overrides
> Cluster Quota Overrides sharing across projects is not supported
> If there are multiple quota overrides for a cluster, the latest matching quota override takes effect
> Override value must be numeric value followed by unit if applicable:
    cpuLimits & cpuRequests: “m“
    memoryLimits & memoryRequests: “Mi“
    storageRequests: “Gi“


- Click **Save Changes**

This allows users to set a different resource quota for the required cluster.  

---
