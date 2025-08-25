---
title: Capabilities 
description: List of Capabilities for VMs
tags:
  - VMs
  - Virtual Machines
  - Capabilities
---

- **Virtual Private Networks (VPCs)**: Organizations can create one or more VPCs within their tenant. Each VPC operates in an isolated network space with its own CIDR range, enabling the reuse of CIDR blocks across different tenants or VPCs without conflict. Isolation is enforced through a dedicated VRF for each VPC.

- **Subnets**: Subnets can be defined within a VPC to support logical network segmentation. Each subnet is mapped to a specific VLAN ID on the underlying infrastructure, providing traffic isolation and improved IP address management.

- **DHCP Support**: Dynamic host configuration is integrated for automated IP address assignment and management within each VPC.

- **Source NAT Rules**: Outbound traffic from a VPC is routed through a tenant-specific IP gateway using Source Network Address Translation.

- **Destination NAT Rules**: Inbound traffic can be controlled using Destination NAT rules to expose selected resources to external systems.

- **Firewall Rules**: Custom firewall rules can be configured to control traffic flow within and across VPCs, supporting granular access policies.

- **DNS Configuration**: DNS traffic is forwarded to a default DNS server defined at the platform level. Optionally, tenants can configure their own private DNS zones if custom resolution is required.

- **Load Balancer Support**: Layer 4 and Layer 7 load balancing is available to distribute traffic efficiently and improve application availability.

This network model provides a flexible, secure foundation for hosting virtual machines in isolated environments, supporting both development and production workloads.


