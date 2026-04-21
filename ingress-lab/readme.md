🚀 Kubernetes Ingress Lab (k3d)

📌 Overview

This lab demonstrates how to configure and troubleshoot an Ingress in Kubernetes using a local k3d cluster.
It highlights real-world issues such as:

•	Missing backends (no pods)
•	Service without endpoints
•	Ingress controller mismatch (Traefik vs NGINX)
•	Path-based routing limitations
________________________________________
🧱 Architecture

•	Kubernetes (k3d / k3s)
•	Ingress Controller: Traefik (default in k3d)
•	2 applications:
o	app1 (nginx)
o	app2 (nginx)
Routing:
•	/app1 → app1-service → pod
•	/app2 → app2-service → pod
________________________________________
🧭 Topology

Client → k3d LoadBalancer → Ingress Controller → Service → Pod
________________________________________
⚙️ Prerequisites

•	Docker
•	kubectl
•	k3d
________________________________________
🚀 Step 1 - Create cluster

k3d cluster create ingress-lab -p "8080:80@loadbalancer"
________________________________________
📦 Step 2 - Deploy applications
kubectl create deployment app1 --image=nginx
kubectl expose deployment app1 --port=80 --name=app1-service

kubectl create deployment app2 --image=nginx
kubectl expose deployment app2 --port=80 --name=app2-service
________________________________________
🌐 Step 3 - Create Ingress

⚠️ Important: k3d uses Traefik by default
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
  - http:
      paths:
      - path: /app1
        pathType: Prefix
        backend:
          service:
            name: app1-service
            port:
              number: 80
      - path: /app2
        pathType: Prefix
        backend:
          service:
            name: app2-service
            port:
              number: 80
kubectl apply -f ingress.yaml
________________________________________
🧪 Step 4 - Test
curl http://localhost:8080/app1
curl http://localhost:8080/app2
________________________________________
⚠️ Issues encountered (real-world debugging)
1. No resources found
Cause: wrong context / empty cluster
2. Endpoints = <none>
Cause: no pods or label mismatch
3. 404 Not Found (Ingress)
Cause: wrong ingressClass (nginx vs Traefik)
4. 404 from nginx
Cause: path /app1 not handled by backend (no rewrite)
________________________________________
🔍 Debug commands
kubectl get pods
kubectl get svc
kubectl get endpoints
kubectl get ingress
kubectl describe ingress
kubectl get all -A
________________________________________
🧠 Key Learnings
•	Ingress ≠ Ingress Controller
•	k3d installs Traefik by default
•	Services require endpoints (pods)
•	404 can come from:
o	Ingress
o	backend application
•	Context and namespace are critical
________________________________________
🧹 Cleanup
k3d cluster delete ingress-lab
________________________________________
📌 Conclusion
This lab demonstrates how small configuration mismatches can lead to real troubleshooting scenarios in Kubernetes.
It reflects real DevOps challenges:
•	environment awareness
•	debugging methodology
•	understanding networking layers


