---
title: Available Configurations
description: Available Configurations for Bare Metal Servers 
tags:
  - Bare Metal Servers
  - Supported Configurations  
---

This page captures supported configurations for bare metal servers. 

<style> .badge { display: inline-block; font-size: 0.7rem; padding: 0.15rem 0.5rem; margin-left: 0.5rem; border-radius: 0.4rem; font-weight: bold; color: white; } .badge-early { background-color: #f59e0b; } .badge-available { background-color: #6366f1; } .gpu-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(340px, 1fr)); gap: 1rem; margin-top: 1.5rem; } .gpu-card { background: #f9fafb; border: 1px solid #e5e7eb; padding: 1rem 1.25rem; border-radius: 0.75rem; box-shadow: 0 2px 6px rgba(0, 0, 0, 0.04); } </style> <div class="gpu-grid"> <div class="gpu-card"> <h4>8× NVIDIA H100 SXM5</h4> <ul> <li>2× Intel Xeon Platinum 8480+ @ 2.0 GHz (224 Threads)</li> <li>2 TB DDR5 4800 MT/s</li> <li>8× H100 SXM5 GPUs (640 GB GPU Memory)</li> <li>NVLink + NVSwitch Interconnect</li> <li>2× 1.92 TB NVMe U.2 Gen5 (System Drive)</li> <li>8× 7.68 TB NVMe U.2 Gen5 (Data Drive)</li> <li>NVIDIA BlueField-3 DPU</li> <li>8× ConnectX-7 Single Port NDR InfiniBand HCA</li> <li>Unlimited Free Ingress & Egress</li> </ul> </div> <div class="gpu-card"> <h4>4× NVIDIA L40S</h4> <ul> <li>2× Intel Xeon Gold 6448Y @ 2.1 GHz (128 Threads)</li> <li>1 TB DDR5 @ 4800 MT/s</li> <li>4× L40S GPUs (192 GB GPU Memory)</li> <li>1× 960 GB NVMe U.2 Gen4 (System Drive)</li> <li>2× 3.84 TB NVMe U.2 Gen4 (Data Drives)</li> <li>NVIDIA BlueField-3 DPU</li> <li>Unlimited Free Ingress & Egress</li> </ul> </div> <div class="gpu-card"> <h4>CPU Node (No GPU)</h4> <ul> <li>2× Intel Xeon Gold 6448Y @ 2.1 GHz (64 Threads)</li> <li>1 TB DDR5-4800 (16× 64GB RDIMM)</li> <li>1× 960 GB NVMe (System Drive)</li> <li>2× 3.84 TB NVMe (Data Drives)</li> <li>NVIDIA BlueField-3 B3220 DPU</li> <li>Dual-Port NDR200 / 200 GbE Networking</li> </ul> </div> </div>

