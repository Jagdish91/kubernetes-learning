# Kubernetes Basics – Minikube & kubectl Commands (WSL)

This document lists **all Minikube and kubectl commands** used while setting up a local Kubernetes cluster and running the first application (Pod) using **WSL (Ubuntu)**.

---

## 🖥 Environment

- OS: Windows + WSL2 (Ubuntu)
- Architecture: amd64
- Container Runtime: Docker Desktop
- Kubernetes: Minikube
- CLI: kubectl

---

## 🔍 System & Architecture Commands

```bash
uname -m
uname
🚀 Minikube Commands
Install Minikube (Official Binary)
bash
Copy code
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64
Verify Minikube Installation
bash
Copy code
minikube version
Start Minikube Cluster
bash
Copy code
minikube start --driver=docker
Docker driver is recommended for WSL environments.

Minikube Status & Info
bash
Copy code
minikube status
minikube profile list
Access Application (later use)
bash
Copy code
minikube service <service-name>
Stop & Delete Minikube Cluster
bash
Copy code
minikube stop
minikube delete
☸️ kubectl Installation Commands
Download kubectl (Official Kubernetes Release)
bash
Copy code
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
Verify kubectl Installation
bash
Copy code
kubectl version --client
☸️ kubectl Cluster Commands
Check Cluster & Nodes
bash
Copy code
kubectl get nodes
kubectl cluster-info
📦 Pod Management Commands
Create Pod Using YAML
bash
Copy code
kubectl create -f pod.yml
Apply Pod (Declarative Way)
bash
Copy code
kubectl apply -f pod.yml
List Pods
bash
Copy code
kubectl get pods
kubectl get pods -o wide
Describe Pod (Debugging)
bash
Copy code
kubectl describe pod nginx
Delete Pod
bash
Copy code
kubectl delete pod nginx
📝 File & YAML Commands Used
bash
Copy code
mkdir kubernetes_learn
cd kubernetes_learn

touch pod.yml
chmod 777 pod.yml
vim pod.yml
cat pod.yml
🌐 Networking & Inspection Commands
bash
Copy code
ip addr
kubectl get pods -o wide
