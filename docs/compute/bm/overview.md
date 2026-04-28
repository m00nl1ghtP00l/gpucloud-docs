---
hide:
  - navigation
  - toc
title: Bare Metal Servers
description: Dedicated Bare Metal GPU servers with maximum performance and control for AI training, inference, and high-performance computing
tags:
  - Bare Metal
  - GPU Servers
  - Dedicated Hardware
  - AI Training
  - Deep Learning
  - NVIDIA GPUs
  - High Performance Computing
  - Machine Learning
  - Inference
---

<style>
  .hero-banner {
    background: linear-gradient(
      135deg,
      var(--md-primary-fg-color) 0%,
      var(--md-accent-fg-color) 100%
    );
    color: var(--md-primary-bg-color);
    padding: 2.5rem 1.5rem;
    border-radius: 0.5rem;
    margin: 2rem 0;
    text-align: center;
  }

  .hero-banner h1 {
    font-size: 2.25rem;
    font-weight: 700;
    margin-bottom: 0.75rem;
    color: var(--md-primary-bg-color);
  }

  .hero-banner p {
    font-size: 1.1rem;
    opacity: 0.95;
    margin-bottom: 0;
  }

  #filter-menu {
    text-align: center;
    margin: 1rem 0 2rem 0;
  }

  #filter-menu button {
    margin: 0.3rem;
    padding: 0.4rem 0.9rem;
    border: none;
    border-radius: 0.25rem;
    background: var(--md-accent-fg-color);
    color: white;
    cursor: pointer;
    font-size: 0.85rem;
  }

  #filter-menu button:hover {
    background: var(--md-primary-fg-color);
  }

  .gpu-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1rem;
    margin: 2rem 0;
  }

  .gpu-card {
    background: var(--md-code-bg-color);
    border-radius: 0.4rem;
    padding: 0.9rem 1rem;
    border-left: 3px solid var(--md-accent-fg-color);
    transition: transform 0.3s ease;
  }

  .gpu-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  }

  .gpu-card h4 {
    font-size: 1.05rem;
    margin-bottom: 0.2rem;
    color: var(--md-accent-fg-color);
  }

  .gpu-card .subtitle {
    font-size: 0.8rem;
    margin-bottom: 0.6rem;
    color: var(--md-default-fg-color--light);
    font-style: italic;
  }

  @media (max-width: 768px) {
    .hero-banner h1 {
      font-size: 1.75rem;
    }

    .gpu-cards {
      grid-template-columns: 1fr;
    }
  }

  .shortcut-card {
    padding: 0.75rem 1.25rem;
    background: var(--md-code-bg-color);
    border-left: 3px solid var(--md-accent-fg-color);
    border-radius: 0.4rem;
    text-decoration: none;
    color: var(--md-default-fg-color);
    font-weight: 500;
    transition: background 0.2s ease;
  }

  .shortcut-card:hover {
    background: var(--md-accent-fg-color);
    color: white;
  }
</style>

<script>
  function filterCards(category) {
    const cards = document.querySelectorAll('.gpu-card');
    cards.forEach(card => {
      const cat = card.getAttribute('data-category');
      card.style.display = (category === 'all' || cat === category) ? 'block' : 'none';
    });
  }
</script>

<div class="hero-banner">
  <h1>Bare Metal GPU Servers</h1>
  <p>
    Dedicated GPU servers with zero virtualization overhead. Maximum performance and complete control for AI training, inference, and high-performance computing workloads.
  </p>
</div>

<div id="filter-menu">
  <button onclick="filterCards('all')">All</button>
  <button onclick="filterCards('performance')">Performance</button>
  <button onclick="filterCards('networking')">Networking</button>
  <button onclick="filterCards('dev')">Dev Experience</button>
  <button onclick="filterCards('management')">Management</button>
  <button onclick="filterCards('hardware')">Hardware</button>
</div>

<div class="gpu-cards">

  <div class="gpu-card" data-category="dev">
    <h4>Self-Service Portal</h4>
    <div class="subtitle">Deploy in Minutes</div>
    Configure, provision, and manage dedicated GPU servers through an intuitive web interface.
  </div>

  <div class="gpu-card" data-category="performance">
    <h4>Latest GPU Hardware</h4>
    <div class="subtitle">H100, A100, L40S, and More</div>
    Access cutting-edge NVIDIA GPUs with full performance and memory capacity.
  </div>

  <div class="gpu-card" data-category="performance">
    <h4>Multi-GPU Configurations</h4>
    <div class="subtitle">Up to 8x GPUs per Server</div>
    Scale with high-density GPU servers featuring NVLink and NVSwitch connectivity.
  </div>

  <div class="gpu-card" data-category="dev">
    <h4>Pre-configured Images</h4>
    <div class="subtitle">Ready for AI/ML Workloads</div>
    Launch with optimized OS images including CUDA, cuDNN, and popular ML frameworks.
  </div>

  <div class="gpu-card" data-category="management">
    <h4>NVMe Storage</h4>
    <div class="subtitle">Local High-Speed Storage</div>
    Direct-attached NVMe SSDs for maximum I/O performance and data throughput.
  </div>

  <div class="gpu-card" data-category="management">
    <h4>Real-time Monitoring</h4>
    <div class="subtitle">Hardware-Level Metrics</div>
    Monitor GPU utilization, temperature, power consumption, and system health.
  </div>

  <div class="gpu-card" data-category="management">
    <h4>Precise Billing</h4>
    <div class="subtitle">Per-Second Metering</div>
    Pay only for actual usage with transparent, granular billing for compute resources.
  </div>

  <div class="gpu-card" data-category="networking">
    <h4>Public Connectivity</h4>
    <div class="subtitle">Direct Internet Access</div>
    Assign public IPs with high-bandwidth internet connectivity for external access.
  </div>

  <div class="gpu-card" data-category="performance">
    <h4>Zero Overhead</h4>
    <div class="subtitle">Native Hardware Performance</div>
    Direct access to GPU hardware without hypervisor penalties or resource contention.
  </div>

  <div class="gpu-card" data-category="performance">
    <h4>High-Speed Interconnects</h4>
    <div class="subtitle">InfiniBand & Ethernet</div>
    Ultra-low latency networking with RDMA support for distributed training and HPC.
  </div>

</div>

