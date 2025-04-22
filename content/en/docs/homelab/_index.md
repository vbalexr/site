---
title: Home Lab
description: High Availability Cluster
tags: [cluster, homelab]
weight: 3
---

This document outlines the configuration and setup of my home lab, focusing on creating a high-availability cluster with low power consumption and modern tools. The goal is to build a reliable, scalable, and efficient environment for personal projects and experimentation.

---

# Goals and Requirements

These are the key requirements and goals I have for my home lab.  
**Note:** This is not my first cluster. I already have enterprise-grade clusters for other purposes. This cluster is specifically for my home and side projects that I enjoy running.

## Low Power Consumption

One of the primary goals is to minimize electricity usage. Running a cluster 24/7 can lead to significant energy costs, especially in a home environment. By choosing energy-efficient hardware, I can ensure that the cluster operates continuously without causing a noticeable increase in electricity bills. This also aligns with sustainability goals and reduces the environmental impact of running a home lab.

## Redundant/Failover Connectivity

Network reliability is critical for any cluster. The system must be resilient to network failures, ensuring that if a single cable or port fails, the cluster remains operational. Redundancy is achieved by using multiple network interfaces and paths, so at least one link remains active at all times. This ensures uninterrupted communication between nodes and external systems.

## High Availability

High availability is a cornerstone of this setup. The cluster must be capable of handling node failures, maintenance, or upgrades without disrupting workloads. This is achieved through distributed systems and orchestration tools that ensure workloads are automatically redistributed to healthy nodes, maintaining uptime and reliability.

## High-Speed Network and Distributed Storage

To support high availability, the cluster requires a high-speed network for efficient communication between nodes. Additionally, a distributed storage system is essential for synchronizing data across nodes. This ensures that data is always accessible, even if one node goes offline. A high-speed network minimizes latency and maximizes throughput, which is critical for data-intensive operations.

## Simple Deployment and Management

Managing the cluster should be straightforward and efficient. By adopting GitOps principles, I can store the entire configuration in a Git repository. This approach provides version control, easy replication, and a clear history of changes. It also simplifies backups and disaster recovery, as the entire setup can be redeployed from the repository.

---

# Hardware

After extensive research, I selected the [Minisforum MS-01](https://store.minisforum.com/products/minisforum-ms-01) MiniPC with an Intel i5-12600H CPU for my cluster. Here’s why this hardware is ideal for my needs:

- **Compact Design**: The small form factor makes it perfect for a home lab, where space is often limited. These MiniPCs can be easily placed on a desk or shelf without taking up much room.
- **Low Power Consumption**: The Intel i5-12600H CPU is energy-efficient, ensuring that the cluster can run continuously without excessive power usage.
- **Networking Options**: Each unit includes multiple networking ports, such as USB4, SFP+, and RJ45, providing flexibility for high-speed and redundant connections.
- **Storage Flexibility**: The MiniPCs feature M.2 NVMe slots for fast storage and a PCIe x8 slot for additional expansion, making them suitable for data-intensive workloads.
- **Scalability**: I purchased three units to create a high-availability cluster. This setup allows for future expansion by adding more nodes as needed.

This hardware strikes a balance between performance, power efficiency, and expandability, making it an excellent choice for a home lab.

---

# Software

Choosing the right software stack was a critical part of the process. I evaluated several options before making a final decision.

## Options Considered

### Bare Metal

Managing systems directly on bare metal was one of the first options I considered.

**Pros**:
- Simple setup with no additional layers of abstraction.
- Familiar from past experience, making it easy to get started.

**Cons**:
- Requires constant manual management, which can be time-consuming.
- Not scalable or efficient for modern workloads.
- Lacks automation, making it unsuitable for a high-availability setup.

**Decision**: Rejected. While bare metal is straightforward, it doesn’t align with my goals of automation and scalability.

---

### Docker

Using Docker containers with Ansible for automation was another option I explored.

**Pros**:
- Widely used and well-documented.
- Simple to set up and manage for single-node environments.
- Containers are lightweight and ideal for modern application deployment.

**Cons**:
- Limited support for high availability across multiple nodes.
- Difficult to balance workloads and manage distributed systems effectively.

**Decision**: Rejected. Docker is great for single-node setups but falls short when it comes to high-availability requirements.

---

### Kubernetes

Kubernetes emerged as the most promising option, despite its complexity.

**Pros**:
- Built-in support for high availability and fault tolerance.
- Automatic load balancing and scaling of workloads.
- A robust ecosystem with tools for managing containerized applications.
- Widely adopted in the industry, ensuring long-term support and community resources.

**Cons**:
- Initial deployment can be complex and requires a learning curve.
- Managing Kubernetes clusters involves understanding new concepts and tools.

**Decision**: Selected. Kubernetes provides the features I need for a high-availability cluster, and I’m willing to invest time in learning and setting it up.

---

## Final Decision: Kubernetes with Talos OS

After deciding on Kubernetes, I looked for ways to simplify its deployment and management. That’s when I discovered [Talos OS](https://www.talos.dev/).

**Why Talos OS?**
- Talos OS abstracts away the underlying operating system, allowing me to focus entirely on Kubernetes.
- It’s designed specifically for modern Kubernetes clusters, with a minimal and secure OS.
- The project has a strong community and is used in production by many organizations.
- Major Kubernetes projects reference and support Talos OS, ensuring compatibility and reliability.

With Talos OS, I can avoid the complexities of managing the operating system and concentrate on building and running my cluster.

---

# Summary

By combining the Minisforum MS-01 hardware with Kubernetes and Talos OS, I’ve created a home lab that meets all my requirements:

- **Low Power Consumption**: Energy-efficient hardware ensures minimal electricity usage.
- **Redundant Connectivity**: Multiple network ports provide failover support.
- **High Availability**: Kubernetes ensures the system remains operational even during maintenance or failures.
- **High-Speed Storage**: Distributed storage with a high-speed network ensures fast and reliable data access.
- **Simple Deployment**: GitOps principles and Talos OS simplify management and deployment.

This setup provides a modern, scalable, and resilient home lab environment that mirrors the capabilities of enterprise-grade systems while remaining cost-effective and easy to manage.

---

# Videos for Reference

To better understand the hardware and software choices, I recommend the following videos:

## Hardware
- [ServeTheHome Review](https://www.youtube.com/watch?v=d3j4aEAZR7w)
- [apalrd's adventures Review](https://www.youtube.com/watch?v=KGQvssq3ee0)

## Talos OS
- [Jim's Garage](https://www.youtube.com/watch?v=TP8hVq1lCxM)
- [Tech Internal Conf](https://www.youtube.com/watch?v=9CIMTum9bTA)