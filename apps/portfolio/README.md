## 📁 Portfolio Application – GitOps Repository

## Overview

This repository manages the deployment of my personal portfolio application using GitOps principles.

The goal of this repo is not to store application source code, but to act as the single source of truth for Kubernetes deployment state, managed by ArgoCD. Actual source code is here - https://github.com/sanjay-k598/sanjay-k598.github.io

All changes to the portfolio infrastructure and Kubernetes resources are applied automatically through GitOps workflows.


## What this repository is responsible for

This repo manages:
	•	Kubernetes manifests for the portfolio application
	•	Namespace creation
	•	Deployment configuration
	•	Service exposure
	•	Ingress configuration
	•	ArgoCD application definition

ArgoCD continuously watches this repository and ensures the cluster state always matches what is defined here.
