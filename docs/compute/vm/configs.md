---
title: Supported Configurations
description: Supported Configurations for GPU based VM
tags:
  - VMs
  - Virtual Machines
  - Supported Configurations  
---

This page provides a summary of supported configurations for Virtual Machines.

<style>
.badge {
  display: inline-block;
  font-size: 0.7rem;
  padding: 0.15rem 0.5rem;
  margin-left: 0.5rem;
  border-radius: 0.4rem;
  font-weight: bold;
  color: white;
}

.badge-early { background-color: #f59e0b; }
.badge-available { background-color: #6366f1; }

.gpu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 1rem;
  margin-top: 1.5rem;
}

.gpu-card {
  background: #f9fafb;
  border: 1px solid #e5e7eb;
  padding: 1rem 1.25rem;
  border-radius: 0.75rem;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.04);
}

[data-md-color-scheme="slate"] .gpu-card {
  background: #1e293b;       
  border: 1px solid #334155;
  color: #f8fafc;            
}

</style>

<div class="gpu-grid">

<div class="gpu-card">
  <h4>NVIDIA B200</h4>
  <ul>
    <li>1× or 8× B200 GPU 180GB SXM</li>
    <li>16× or 128× vCPU Intel Emerald Rapids</li>
    <li>224 or 1792 GB DDR5</li>
    <li>3.2 Tbit/s InfiniBand</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA H200 </h4>
  <ul>
    <li>1× or 8× H200 GPU 141GB SXM</li>
    <li>16× or 128× vCPU Intel Sapphire Rapids</li>
    <li>200 or 1600 GB DDR5</li>
    <li>3.2 Tbit/s InfiniBand</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA H100 </h4>
  <ul>
    <li>1× or 8× H100 GPU 80GB SXM</li>
    <li>16× or 128× vCPU Intel Sapphire Rapids</li>
    <li>200 or 1600 GB DDR5</li>
    <li>3.2 Tbit/s InfiniBand</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA L40S (Intel) </h4>
  <ul>
    <li>1× L40S GPU 48GB PCIe</li>
    <li>8× or 40× vCPU Intel Xeon Gold</li>
    <li>32 or 160 GB DDR5</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA L40S (AMD) </h4>
  <ul>
    <li>1× L40S GPU 48GB PCIe</li>
    <li>16× or 192× vCPU AMD EPYC</li>
    <li>96 or 1152 GB DDR5</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA A100</h4>
  <ul>
    <li>1× or 8× A100 GPU 40GB or 80GB (SXM or PCIe)</li>
    <li>16× to 128× vCPU Intel Cascade Lake or Milan</li>
    <li>256 to 2048 GB DDR4/DDR5</li>
    <li>3.2 Tbit/s InfiniBand or 100 Gbps Ethernet</li>
    <li>Ubuntu 20.04 / 22.04 LTS (CUDA® 11/12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA A40</h4>
  <ul>
    <li>1× A40 GPU 48GB PCIe</li>
    <li>8× to 64× vCPU Intel Xeon Gold / EPYC</li>
    <li>128 to 1024 GB DDR4/DDR5</li>
    <li>10/25/100 Gbps Ethernet</li>
    <li>Ubuntu 20.04 / 22.04 LTS (CUDA® 11/12)</li>
  </ul>
</div>

<div class="gpu-card">
  <h4>NVIDIA T4</h4>
  <ul>
    <li>1× T4 GPU 16GB PCIe</li>
    <li>8× to 32× vCPU Intel Xeon / AMD EPYC</li>
    <li>64 to 512 GB DDR4</li>
    <li>10/25 Gbps Ethernet</li>
    <li>Ubuntu 20.04 LTS (CUDA® 11)</li>
  </ul>
</div>


<div class="gpu-card">
  <h4>NVIDIA L4</h4>
  <ul>
    <li>1× L4 GPU 24GB PCIe</li>
    <li>8× to 32× vCPU Intel Xeon / AMD EPYC</li>
    <li>128 to 512 GB DDR5</li>
    <li>25 Gbps Ethernet or local NVMe</li>
    <li>Ubuntu 22.04 LTS (CUDA® 12)</li>
  </ul>
</div>

</div>

--- 

## By Use Case

End users can select the VM configuration best suited for on their computational requirements. 

### **Single GPU (1x)**
Perfect for development, prototyping, and small-scale inference

### **Dual GPU (2x)**
Ideal for medium-scale training and distributed workloads

### **Quad GPU (4x)**
Designed for large-scale training and high-performance computing

---

## By GPU Type/Model 

### Nvidia H100 SXM
80GB HBM3 memory per GPU, optimized for AI/ML workloads

### Nvidia L40S
48GB GDDR6 memory per GPU, ideal for inference and training



<!---
Back Button
-->
[← Back](../../index.md){ .md-button .md-button--primary }

