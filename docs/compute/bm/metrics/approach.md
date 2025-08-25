---
title: GPU and Host Metrics for Bare Metal Servers
description: Enabling End User facing GPU and Bare Metal Server Metrics
tags:
  - Bare Metal Servers
  - Metrics
  - Monitoring  
---

The image below outlines the architecture and approach used by Rafay to centrally aggregate GPU and Server telemetry from end user bare metal servers hosted in the cloud provider's datacenter. The metrics are aggregated using [OpenTelemetry (OTel)](https://opentelemetry.io/) and synchronized to a centralized **Time Series Database** at the Rafay Controller for end-user visualization and analytics.

![Metrics Flow Architecture](../metrics/img/bm_metrics_pipeline.png)

!!! info
    Only Ubuntu 22.04 and 24.04 OS based Bare Metal Servers are currently supported for integrated metrics. 

--- 

## Key Capabilities 

### Open Standards
Uses OpenTelemetry for portability and extensibility

### Multi-Server Scaling
Architecture supports deployment across many bare metal servers

### Tenant Isolation
Metrics collected per-host, enabling multi-tenant observability

### No Kernel Modules
All exporters and collectors run in user space

---

## Central Time Series Database

Metrics data from all the bare metal servers under management is aggregated in a time series database co-located on the Rafay Controller. This centralized telemetry backend: 

1. Stores time-series data from all bare metal servers
2. Supports querying and dashboard rendering
3. Implements retention and downsampling policies

--- 

## Components

The following modules are used for metrics aggregation at the bare metal server. 


### **NVIDIA DCGM Exporter**  

This component collects GPU-related metrics such as:

- Memory utilization
- Core utilization
- Temperature
- Health status

### **Host Metrics Exporter**  

This component collects system-level metrics including:

- CPU usage
- Memory usage
- Disk I/O
- Network statistics

### **OpenTelemetry (OTel) Collector**  

This is operated as a local service on the bare metal server. 

- It scrapes data from the DCGM and Host Metrics exporters
- Normalizes and prepares metrics
- Forwards metrics to the central TSDB at the Rafay Controller

!!! important
    By default, metrics data is aggregated from the bare metal server to the centralized TSDB **every 60 seconds**. 

---




