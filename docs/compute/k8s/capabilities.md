---
title: Capabilities of the Managed Kubernetes Service
description: Overview of capabilities supported by the Managed Kubernetes Service for running and managing Kubernetes clusters 
tags:
  - Managed Kubernetes
  - Kubernetes Automation
  - Multi-cloud
  - Infrastructure Management
  - Clusters
  - Enterprise Kubernetes
  - Cloud-native
---

The Managed Kubernetes Service provides a robust set of capabilities for provisioning, operating, and scaling Kubernetes clusters. It simplifies the end-to-end lifecycle management of clusters with features designed for reliability, automation, and operational efficiency.

--- 

## Provisioning

- One-click provisioning of managed Kubernetes clusters.
- Supports Highly Available (HA) and non-HA control plane configurations.
- Master and worker nodes can be provisioned on VM, Bare Metal, or other physical infrastructure.
- Option to enable SSH for master/worker nodes.
- Blueprint applied automatically during provisioning.
- Control plane nodes can be placed across regions or availability zones based on selected infrastructure SKUs.

## Networking

- Supports Calico CNI for cluster networking.
- Supports proxy configuration for outbound network access.
- Automatic IP allocation for all node pools.

## Access Control

- Kubeconfig is automatically generated during provisioning.
- Role-based access controls can be applied via blueprints or post-provisioning.

## GPU Support

- GPU injection is handled through blueprints.
- Only GPU types supported in the selected blueprint can be used.

## Blueprints

- Support for default and custom blueprint versions.
- Automatic application of blueprint-defined system components (e.g., logging, monitoring).

## Scaling

- Worker node scaling is supported.
- Nodes are removed using LIFO (Last-In-First-Out) policy when scaling down.
- Scale operations can be triggered via the UI or APIs.

## Upgrades

- Kubernetes version upgrades supported for worker nodes.
- Control plane upgrades are configurable during provisioning.

## Automation

- Workflow handlers can be attached for advanced automation use cases.
- Supports provisioning through Rafay APIs, Terraform, or cloud-init.

## Multi-Infrastructure Support

- Supports infrastructure SKUs on VM, Bare Metal, and physical nodes.

## Tagging and Annotations

- Supports tagging for all resources (master, worker, and control plane).
- Node-level annotations supported.

## Day-2 Operations

- View cluster and node metadata.
- Download kubeconfig for cluster access.
- Perform scale and upgrade operations.
- Attach new worker pools post-deployment.

## Outputs

- Kubeconfig
- Master and worker node details
- Network configuration
- Private key for SSH access (if enabled)

## Monitoring and Validation

- Region compatibility checks during provisioning.
- Validations for runtime dependencies and supported configurations.
- Access to node discovery and provisioning logs.
