🏠 Homelab GitOps Platform (Kubernetes + Argo CD)

A hands-on GitOps implementation running on a self-hosted Kubernetes homelab using Argo CD.
This repository is the single source of truth for everything deployed to the cluster.

All changes flow through Git.
No manual kubectl apply. No drift.

⸻

⚙️ What This Repo Does
	•	Manages Kubernetes apps declaratively
	•	Uses Argo CD for continuous reconciliation
	•	Automatically rolls out changes when Git updates
	•	Exposes apps using Traefik + nip.io
	•	Mirrors real production GitOps workflows

⸻

🔁 GitOps Flow (High Level)

Code Change → GitHub → Argo CD → Kubernetes
                     ↑
                Docker Hub

	•	CI builds and pushes images to Docker Hub
	•	CD pulls desired state from this repo
	•	Argo CD keeps the cluster in sync with Git

⸻

📁 Repo Structure

apps/
└── portfolio/
    ├── namespace.yaml
    ├── deployment.yaml
    ├── service.yaml
    └── ingress.yaml

Each app is isolated, declarative, and fully managed by Argo CD.

⸻

🚀 Live Example

Portfolio App
	•	Namespace: portfolio
	•	Replicas controlled via Git
	•	Auto rollout on manifest change
	•	Accessible via Traefik ingress

http://portfolio.192.168.1.70.nip.io


⸻

🧠 What This Shows
	•	Real GitOps behavior (not demo scripts)
	•	Clear CI vs CD separation
	•	Kubernetes reconciliation in action
	•	Argo CD health, sync, and drift handling
	•	Production-style repo layout

⸻

🛠 Tech Stack
	•	Kubernetes (K3s)
	•	Argo CD
	•	GitHub
	•	Docker Hub
	•	Traefik Ingress
	•	nip.io DNS

⸻

👤 Author

Sanjay Kumar Khambam
Senior DevOps / Cloud Engineer
GitOps • Kubernetes • Platform Engineering

⸻
	•	Align this README with specific job roles (Platform / SRE / DevOps)

This version is fast to read, visually clear, and interview-ready.
