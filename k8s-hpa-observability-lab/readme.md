# Kubernetes HPA + Load Testing + Monitoring Lab

## Overview

This lab demonstrates how to implement and observe **Horizontal Pod Autoscaling (HPA)** in Kubernetes using:

- Kubernetes HPA
- Metrics Server
- Prometheus
- Grafana
- Load testing with `hey`

You will learn how to:

- Deploy a CPU-intensive application
- Configure autoscaling based on CPU usage
- Generate traffic/load
- Observe scaling behavior in real time
- Monitor pods and cluster metrics with Grafana

Based on the lab guide provided in the PDF document.

---

# Architecture

The lab architecture includes:

- A Kubernetes Deployment
- A Service exposing the application
- Metrics Server for CPU metrics
- HPA controller
- Prometheus for metrics collection
- Grafana dashboards for visualization

## Main scaling flow

```text
Load → CPU Usage ↑ → Metrics Server → HPA → More Pods
```

---

# Repository Structure

```text
k8s-hpa-observability-lab/
│
├── app/
│   ├── deployment.yaml
│   └── service.yaml
│
├── hpa/
│   └── hpa.yaml
│
├── monitoring/
│   └── prometheus-grafana.yaml
│
└── README.md
```

---

# Prerequisites

- Kubernetes cluster (k3d, k3s, Minikube, EKS, etc.)
- kubectl
- Helm
- Docker
- Metrics Server
- Prometheus + Grafana
- hey (load testing tool)

# screenshots

![EC2 Instances](images/cluster-CPU.png)

