# 🚀 Kubernetes Labs

This repository contains a collection of **hands-on Kubernetes labs** focused on real-world cloud-native concepts.

The goal is to build practical experience with:

* Kubernetes core concepts
* Networking (Ingress)
* Observability (Prometheus & Grafana)
* GitOps (Argo CD — see dedicated repo)

---

## 📁 Labs Overview

### 🌐 Ingress Lab

Implementation of external access to services using Kubernetes Ingress.

**Key concepts:**

* Ingress resource configuration
* HTTP routing to services
* NGINX Ingress Controller
* Service exposure without NodePort

**What was done:**

* Deployed an application (nginx)
* Exposed it via Ingress
* Configured routing rules
* Tested access through browser

---

### 📊 Observability Lab (Prometheus + Grafana)

Implementation of a basic monitoring stack inside Kubernetes.
https://github.com/guihen01/kubernetes-labs/tree/main/k8s-observability

**Key concepts:**

* Metrics collection
* Prometheus scraping
* Grafana dashboards
* Service monitoring

**What was done:**

* Installed Prometheus
* Configured metrics scraping
* Installed Grafana
* Connected Grafana to Prometheus
* Visualized cluster metrics

---
## 📊 Observability Labs

Advanced observability labs are hosted in separate repositories to reflect real-world architecture.

* App Observability Lab (Python + Prometheus + Grafana)
  → https://github.com/guihen01/app-observability-lab

--

### 🔁 GitOps Lab (Argo CD)

👉 This lab is available in a dedicated repository:

🔗 https://github.com/guihen01/argo-lab

**Concepts:**

* Git as source of truth
* Continuous deployment with Argo CD
* Automated sync & self-healing

---

## 🧠 Skills Demonstrated

* Kubernetes resource management (Deployment, Service, Ingress)
* Cluster networking concepts
* Observability and monitoring setup
* GitOps workflows with Argo CD
* YAML-based infrastructure definition

---

## 🏗️ Technologies Used

* Kubernetes (k3d / local cluster)
* kubectl
* NGINX Ingress Controller
* Prometheus
* Grafana
* Argo CD

---

## 🚀 Learning Approach

These labs are:

* Hands-on
* Built from scratch
* Focused on understanding real behavior (not just theory)

---

## 📌 Next Steps

* Helm integration
* Multi-environment deployments (dev / prod)
* Advanced observability (alerts, custom metrics)
* CI/CD pipelines integration

---

## 💡 About

This repository is part of a broader effort to build strong expertise in:

* Cloud Engineering
* DevOps practices
* Kubernetes ecosystem

---

## ⭐ Author

**Henri Guillot**
Cloud & Network Engineer



