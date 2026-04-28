
# 🚀 Kubernetes GitOps Lab with Argo CD (k3d)

## Overview
This lab demonstrates a GitOps workflow using Kubernetes and Argo CD.

Flux continuously synchronizes a Kubernetes cluster with the desired state defined in a Git repository.

## Argo CD & git Lab

➡️ See dedicated repo: https://github.com/guihen01/argo-lab

## Key Idea
Git → Flux → Kubernetes

Any change pushed to Git is automatically applied to the cluster.

## Steps
- Create k3d cluster
- Install Flux
- Bootstrap GitHub repo
- Deploy nginx via Git
- Modify replicas → auto update

## Verify
kubectl get pods

## Cleanup
k3d cluster delete gitops-lab
EOF
