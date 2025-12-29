# Kubernetes Monitoring with ArgoCD, Prometheus & Grafana

This directory contains a production-style Kubernetes monitoring stack deployed using **GitOps principles** with ArgoCD.  
The setup provides **cluster observability, persistent Grafana dashboards, and safe credential management**.

The goal of this setup is not just to install monitoring, but to demonstrate **operability, recovery, and real-world troubleshooting**.

---

## Architecture Overview

This monitoring stack is deployed using the `kube-prometheus-stack` Helm chart and managed entirely by ArgoCD.

**Key characteristics:**
- Fully GitOps-managed (no manual kubectl applies)
- Persistent Grafana data across pod restarts
- Kubernetes-native secrets for credentials
- Automated reconciliation and self-healing via ArgoCD

---

## Components Used

- **ArgoCD** – GitOps deployment, drift detection, and self-healing
- **Prometheus Operator** – Metrics collection and lifecycle management
- **Prometheus** – Time-series metrics storage
- **Grafana** – Visualization and dashboards
- **Kubernetes PVCs** – Persistent storage for Grafana and Prometheus
- **Kubernetes Secrets** – Secure handling of Grafana admin credentials

---



## 📸 Screenshots

All screenshots are taken from the **live cluster** and committed to this repository for transparency.

---

## ArgoCD

### Monitoring Application – Healthy & Synced

<img src="screenshots/01-argocd-monitoring-health.png" width="100%" />

[Open full-size image](screenshots/01-argocd-monitoring-health.png)

### ArgoCD – Monitoring Application (Healthy & Synced)

> Click the image to view full resolution

[![ArgoCD Monitoring App](./screenshots/01-argocd-monitoring-healthy.png)](./screenshots/01-argocd-monitoring-healthy.png)
---

### ArgoCD Resource Tree

<img src="screenshots/02-argocd-monitoring-tree.png" width="100%" />

[Open full-size image](screenshots/02-argocd-monitoring-tree.png)

---

## Prometheus

### Node Exporter Targets (UP)

<img src="screenshots/03-nodeexporter.png" width="100%" />

[Open full-size image](screenshots/03-nodeexporter.png)

---

### Prometheus Targets – Healthy

<img src="screenshots/06-prometheus-targets-up.png" width="100%" />

[Open full-size image](screenshots/06-prometheus-targets-up.png)

---

## Grafana

### Prometheus Datasource Connected

<img src="screenshots/04-grafana-datasource-prometheus.png" width="100%" />

[Open full-size image](screenshots/04-grafana-datasource-prometheus.png)

---

### Kubernetes Cluster Dashboard

<img src="screenshots/05-grafana-dashboard-k8s-cluster.png" width="100%" />

[Open full-size image](screenshots/05-grafana-dashboard-k8s-cluster.png)

---
## Repository Structure

```text
apps/monitoring/
├── application.yaml        # ArgoCD Application definition
├── helm/
│   └── values.yaml         # Helm values for kube-prometheus-stack
├── ingress/
│   └── grafana-ingress.yaml
├── namespace.yaml
└── README.md

```

---

## Persistence & Recovery 

Grafana uses a PersistentVolumeClaim backed by the local-path storage class.
Dashboards, users, and settings survive pod restarts.

Tested by:
- Deleting the Grafana pod
- Verifying dashboards and data remained intact

---

## Secrets Handling

Grafana admin credentials are stored in a Kubernetes Secret
and injected via Helm values using existingSecret.

Secrets are not hardcoded in Git.

•	ArgoCD application in Healthy state

---


## Future Improvements 

Planned improvements:
- Application-level metrics via ServiceMonitor
- Ingress metrics dashboards
- Alerting rules for critical conditions
- Loki for log aggregation


