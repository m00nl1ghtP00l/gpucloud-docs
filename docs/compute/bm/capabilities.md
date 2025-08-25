---
title: Capabilities of the Bare Metal GPU Servers
description: Overview of capabilities supported by the Bare Metal GPU Servers for running high-performance AI/ML workloads.
tags:
  - Bare Metal GPU Server
  - Capabilities
---

The following capabilities are supported as part of the Bare Metal GPU Servers 

| Capability                         | Description                                                                 |
|------------------------------------|-----------------------------------------------------------------------------|
| **Multi-GPU Support**              | Enables usage of nodes with 1, 4, or 8 high-performance GPUs for scale-out training and inference workloads. |
| **Kubernetes Integration**         | Supports Kubernetes-native workflows; users can deploy workloads using standard manifests and Helm charts. |
| **Custom OS Images**               | Ability to boot bare metal nodes with pre-approved base operating systems such as Ubuntu 22.04 LTS. |
| **GPU Sharing (Optional)**         | Offers full node access, but can also support GPU sharing configurations when enabled at cluster level. |
| **High-Speed Interconnects**       | Nodes are equipped with NVLink, NVSwitch, and NDR Infiniband for high-bandwidth GPU-to-GPU communication. |
| **Dedicated CPU Nodes**           | Allows provisioning of CPU-only nodes for non-GPU workloads such as orchestration, preprocessing, or storage. |
| **User-Controlled Lifecycle**      | End users can start, stop, and terminate nodes through self-service controls with quota enforcement. |
| **Custom Initialization Hooks**    | Supports bootstrap scripts and environment-specific initialization logic. |
| **Telemetry & Monitoring**         | Integration with monitoring dashboards and system metrics for observability (requires setup). |
| **Networking & Security**          | Supports workload isolation through Kubernetes namespaces, CNI-based policies, and secure ingress/egress. |
| **No Virtualization Overhead**     | Direct access to hardware ensures maximum performance for demanding AI/ML pipelines. |

---


