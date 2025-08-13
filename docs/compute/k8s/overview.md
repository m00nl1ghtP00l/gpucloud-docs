---
hide:
  - navigation
  - toc
title: Compute Cloud - Managed Kubernetes Clusters as a Service 
description: A fully managed, Kubernetes based container orchestrator optimized for modern AI workloads.
tags:
  - Kubernetes 
  - Managed Kubernetes
  - GPU PaaS
  - Self Service 
  - Cloud Providers
  - AI Training
  - Deep Learning
  - NVIDIA GPUs
  - High Performance Computing
---

<style>
  .hero-banner {
    background: linear-gradient(135deg, var(--md-primary-fg-color) 0%, var(--md-accent-fg-color) 100%);
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
    box-shadow: 0 4px 15px rgba(0,0,0,0.08);
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
  <h1>Managed Kubernetes Clusters as a Service</h1>
  <p>GPU-accelerated, fully managed container orchestrator optimized for modern AI workloads</p>
</div>

<div id="filter-menu">
  <button onclick="filterCards('all')">All</button>
  <button onclick="filterCards('performance')">Performance</button>
  <button onclick="filterCards('dev')">Dev Experience</button>
  <button onclick="filterCards('management')">Management</button>
  <button onclick="filterCards('networking')">Networking</button>
  <button onclick="filterCards('security')">Security</button>
</div>

<div class="gpu-cards">

<div class="gpu-card" data-category="dev">
  <h4>End User Self Service</h4>
  <div class="subtitle">Simple and Intuitive</div>
  End user self-service experience to configure, launch and use a Managed Kubernetes Cluster with GPUs.
</div>

<div class="gpu-card" data-category="management">
  <h4>Multi-Version Support</h4>
  <div class="subtitle">Stay Current</div>
  Support for multiple Kubernetes versions with automated upgrade paths and rollback capabilities.
</div>

<div class="gpu-card" data-category="management">
  <h4>High Availability Control Plane</h4>
  <div class="subtitle">99.9% Uptime SLA</div>
  Multi-master setup with automated failover and distributed etcd for maximum reliability.
</div>

<div class="gpu-card" data-category="management">
  <h4>Automated Cluster Lifecycle</h4>
  <div class="subtitle">Hands-Off Operations</div>
  Automated cluster provisioning, scaling, upgrades, and patching with zero downtime.
</div>

<div class="gpu-card" data-category="networking">
  <h4>CNI Plugin Support</h4>
  <div class="subtitle">Flexible Networking</div>
  Choose from Cilium, Calico, or Flannel for pod networking and network policies.
</div>

<div class="gpu-card" data-category="security">
  <h4>RBAC & Security Policies</h4>
  <div class="subtitle">Enterprise Security</div>
  Built-in RBAC, Pod Security Standards, and Network Policy enforcement.
</div>

<div class="gpu-card" data-category="security">
  <h4>Rafay Zero Trust Kubectl</h4>
  <div class="subtitle">Secure Developer Access</div>
  Enforce Zero Trust principles for `kubectl` access using Rafay's Access Proxy with centralized authorization, auditing, and identity-based access controls—without VPN or bastion hosts.
</div>

<div class="gpu-card" data-category="networking">
  <h4>Load Balancer Integration</h4>
  <div class="subtitle">Automatic Load Balancing</div>
  Native integration with cloud load balancers and ingress controllers.
</div>

<div class="gpu-card" data-category="performance">
  <h4>Latest GPUs</h4>
  <div class="subtitle">From NVIDIA, AMD, and Intel</div>
  Support for state-of-the-art GPU models such as H100, A100, and more.
</div>

<div class="gpu-card" data-category="dev">
  <h4>AI/ML Ready</h4>
  <div class="subtitle">Quick Deployments</div>
  Accelerate setup with pre-installed GPU Operator for Kubernetes.
</div>

<div class="gpu-card" data-category="management">
  <h4>Integrated Metrics</h4>
  <div class="subtitle">Real-Time Usage Monitoring</div>
  View Kubernetes metrics and GPU metrics from the user console.
</div>

<div class="gpu-card" data-category="management">
  <h4>Metering</h4>
  <div class="subtitle">Accurate Resource Accounting</div>
  Precise, per-second metering for tracking resource usage to support billing and reporting.
</div>

<div class="gpu-card" data-category="management">
  <h4>Block Storage</h4>
  <div class="subtitle">Integrated Storage</div>
  Turnkey integration with CSIs from Rook/Ceph, DDN, Weka, Vast Data and others.
</div>


</div>

<!---
Back Button
-->
[← Back](../../index.md){ .md-button .md-button--primary }
