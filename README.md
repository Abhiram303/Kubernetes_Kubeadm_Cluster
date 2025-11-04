# 🚀 Kubernetes Cluster Setup using Kubeadm
This document explains how to set up a **Kubernetes cluster** from scratch using **kubeadm**, **containerd**, and **Calico** networking on **AWS EC2 instances**.

---

## 🧠 Overview

There are several tools for setting up Kubernetes clusters, including:

- **kubeadm**
- **Cluster API**
- **kOps**
- **Kubespray**

Here, I’ll use **kubeadm**, a lightweight and official way to bootstrap a cluster.

---

## 🧩 Prerequisites

### System Requirements
- Compatible Linux host (Debian or RHEL-based).
- **2 GB RAM minimum** per node (more recommended).
- **2 vCPUs** or more for control plane node.
- **Full network connectivity** between all nodes.
- **Unique hostname, MAC address, and product UUID** per node.

---

## ☁️ AWS Infrastructure Setup

Create **three EC2 instances** (Ubuntu recommended):

| Node Type | Name | Purpose |
|------------|-------|----------|
| Control Plane | `k8master` | Master node |
| Worker Node 1 | `k8worker-1` | Worker node |
| Worker Node 2 | `k8worker-2` | Worker node |

Also create an **Elastic IP** for the Master node.

---

## ⚙️ Basic Configuration on All Nodes

### 1. Set Hostnames (to avoid confusion , name the nodes as per your understanding as we are going to run the installation steps parallelly to some extinct)

```bash
sudo hostnamectl set-hostname k8master    # On master
sudo hostnamectl set-hostname k8worker-1  # On worker 1
sudo hostnamectl set-hostname k8worker-2  # On worker 2
```

### 2. Update /etc/hosts
