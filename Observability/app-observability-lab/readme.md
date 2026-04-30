# Kubernetes Observability Lab (Python + Prometheus + Grafana)

This lab demonstrates a complete observability pipeline in Kubernetes using a custom Python application.

---

## 🔗 Full Lab Repository

👉 https://github.com/guihen01/app-observability-lab

---

## 🧠 What this lab covers

* Application instrumentation with Prometheus client
* Custom metrics exposure (`/metrics`)
* ServiceMonitor integration (Prometheus Operator)
* Metrics scraping with Prometheus
* Visualization with Grafana
* Kubernetes deployment (Deployment / Service / Ingress)

---

## 📊 Architecture

User → Ingress → Service → Python App
↓
/metrics
↓
Prometheus
↓
Grafana

---

## 💡 Key Insight

Without proper instrumentation and ServiceMonitor configuration,
Prometheus cannot detect or scrape application metrics.

---

## 🚀 Why this matters

Modern cloud-native systems require:

* observability (not just deployment)
* real-time metrics visibility
* integration between application and monitoring stack

---

👉 Full implementation available in the repository above.

