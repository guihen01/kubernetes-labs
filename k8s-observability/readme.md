
# 🚀 Kubernetes Observability Lab — Prometheus + Grafana

## 🎯 Overview

This lab demonstrates how to build a complete observability stack on Kubernetes using:

* Prometheus for metrics collection
* Grafana for visualization
* Helm for deployment
* A sample application to monitor

---
## 📸 Screenshots



## 🧭 Objectives

* Install Helm
* Deploy Prometheus & Grafana on Kubernetes
* Understand how metrics scraping works
* Explore dashboards
* Apply debugging and inspection techniques

---

## 🧱 Architecture

```
Pod → Service → ServiceMonitor → Prometheus → Grafana
```

---

## ⚙️ Prerequisites

* Kubernetes cluster (minikube or k3d)
* kubectl
* Internet access

---

## 🛠️ Step 0 — Install Helm

### Check if Helm is installed

```bash
helm version
```

### Install Helm (Linux)

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

### Verify

```bash
helm version
kubectl version --client
```

---

## 📦 Step 1 — Install Prometheus Stack

### Add Helm repo

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

### Create namespace

```bash
kubectl create namespace monitoring
```

### Install

```bash
helm install monitoring prometheus-community/kube-prometheus-stack \
  --namespace monitoring
```

---

## 🔍 Step 2 — Inspect Resources

```bash
kubectl get all -n monitoring
kubectl get svc -n monitoring
```

### Inspect a service

```bash
kubectl describe svc monitoring-grafana -n monitoring
```

### View logs

```bash
kubectl logs -n monitoring <pod-name>
```

---

## 📊 Step 3 — Access Grafana

### Get admin password

```bash
kubectl get secret monitoring-grafana \
  -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decode
```

### Port-forward

```bash
kubectl port-forward svc/monitoring-grafana 3000:80 -n monitoring
```

👉 Open: http://localhost:3000
Login: **admin**

---

## 📈 Step 4 — Explore Dashboards

Go to **Dashboards → Browse**

Explore:

* Kubernetes Cluster
* Node metrics
* Pod metrics

---

## 🔎 Step 5 — Access Prometheus

```bash
kubectl port-forward svc/monitoring-kube-prometheus-prometheus 9090 -n monitoring
```

👉 Open: http://localhost:9090

### Test query

```promql
up
```

👉 Go to: **Status → Targets**

---

## 🚀 Step 6 — Deploy Sample App

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: demo-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: demo-app
  template:
    metadata:
      labels:
        app: demo-app
    spec:
      containers:
      - name: demo-app
        image: nginx
        ports:
        - containerPort: 80
```

```bash
kubectl apply -f app.yaml
```

---

## 🌐 Step 7 — Expose Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: demo-app
  labels:
    app: demo-app
spec:
  selector:
    app: demo-app
  ports:
    - name: http
      port: 80
      targetPort: 80
```

---

## 📡 Step 8 — Create ServiceMonitor

```yaml
apiVersion: monitoring.coreos.com/v1
kind: ServiceMonitor
metadata:
  name: demo-app
  labels:
    release: monitoring
spec:
  selector:
    matchLabels:
      app: demo-app
  endpoints:
    - port: http
      interval: 15s
```

---

## ✅ Step 9 — Verify Metrics

In Prometheus:

```promql
up{job="demo-app"}
```

👉 Check: **Status → Targets**

---

## ⚠️ Common Pitfalls

* Helm not installed
* Wrong namespace
* Missing port name in Service
* ServiceMonitor label mismatch
* App without metrics endpoint

---

## 🧠 Key Concepts

* Prometheus scrapes metrics from services
* Grafana queries Prometheus
* ServiceMonitor defines what to scrape
* Kubernetes labels are critical

---

## 🎉 Expected Outcome

* Prometheus running and scraping targets
* Grafana dashboards available
* Kubernetes resources correctly deployed
* Observability pipeline functional

---

## 🚀 Next Steps

* Add a real metrics-enabled app (Python / Go)
* Create custom Grafana dashboards
* Configure alerting (Alertmanager)
* Deploy using GitOps (ArgoCD)

---

## 💼 Resume / LinkedIn Highlight

Built a Kubernetes observability stack using Prometheus and Grafana, including Helm deployment, ServiceMonitor configuration, and metrics visualization.
