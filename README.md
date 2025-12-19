# 🏠 Homelab GitOps Platform (Kubernetes + Argo CD)

A hands-on **GitOps implementation** running on a self-hosted Kubernetes homelab using **Argo CD**.  
This repository is the **single source of truth** for everything deployed to the cluster.

All changes flow through Git.  
No manual `kubectl apply`.  
No configuration drift.

---

## 🧭 Architecture Overview

> GitHub → Argo CD → Kubernetes  
> Docker images are pulled from Docker Hub at runtime.

![GitOps Architecture](./docs/gitops-architecture.png)

_(Sketch-style diagram showing GitHub, Argo CD, Docker Hub, and Kubernetes reconciliation flow)_

---

## ⚙️ What This Repo Does

- Manages Kubernetes applications declaratively
- Uses Argo CD for continuous reconciliation
- Automatically rolls out changes when Git updates
- Exposes apps using Traefik + nip.io
- Mirrors real production GitOps workflows

This is not a demo script.  
This is a working GitOps platform.

---

## 🔁 GitOps Flow (High Level)

Code Change → GitHub → Argo CD → Kubernetes
↑
Docker Hub

- CI builds and pushes images to Docker Hub
- CD pulls desired state from this repository
- Argo CD keeps the cluster in sync with Git

---

## 📁 Repository Structure
- CI builds and pushes images to Docker Hub
- CD pulls desired state from this repository
- Argo CD keeps the cluster in sync with Git

---

## 📁 Repository Structure

apps/
└── portfolio/
├── namespace.yaml
├── deployment.yaml
├── service.yaml
└── ingress.yaml

Each application is:
- Isolated by namespace
- Fully declarative
- Continuously reconciled by Argo CD

---

## 🚀 Live Example

**Portfolio Application**

- Namespace: `portfolio`
- Replicas controlled via Git
- Automatic rollout on manifest change
- Exposed via Traefik ingress

🌐 **Access URL**  
http://portfolio.192.168.1.70.nip.io

---

## 🧠 What This Demonstrates

- Real GitOps behavior (not manual deployments)
- Clear separation of CI and CD
- Kubernetes reconciliation in action
- Argo CD health, sync, and drift handling
- Production-style repository layout

This setup reflects how modern platform teams operate.

---

## 🛠 Tech Stack

- Kubernetes (K3s)
- Argo CD
- GitHub
- Docker Hub
- Traefik Ingress
- nip.io DNS

---

## 👤 Author

**Sanjay Kumar Khambam**  
Senior DevOps / Cloud Engineer  

GitOps • Kubernetes • Platform Engineering

---

## 📌 Notes

This repository is part of an ongoing homelab platform used to:
- Experiment with GitOps patterns
- Validate production-grade workflows
- Showcase real-world Kubernetes operations

