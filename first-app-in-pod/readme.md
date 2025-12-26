# Kubernetes Learning – Minikube & kubectl (Complete Command Log)

This README contains a complete, end-to-end list of **all commands executed** while learning Kubernetes basics using **Minikube** and **kubectl** inside **WSL (Ubuntu)** on Windows.

Nothing is skipped. This file serves as a **learning log + reference**.

---

## Environment

- Windows with WSL2 (Ubuntu)
- Architecture: amd64
- Container Runtime: Docker Desktop
- Kubernetes: Minikube
- CLI: kubectl

---

## Complete Command History

```bash
# create working directory
mkdir kubernetes_learn
cd kubernetes_learn/
ls

# try starting minikube (initial attempt)
minikube start --driver=wsl2

# check system architecture and OS
uname -m
uname

# download minikube (official)
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64

# install minikube
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64

# verify minikube binary
ls /usr/local/bin/
ls /usr/local/bin/minikube
ls -l /usr/local/bin/minikube
minikube version

# download kubectl (official)
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

# install kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# verify kubectl
kubectl version --client

# start minikube using docker driver
minikube start --driver=docker

# verify cluster
kubectl get nodes

# create pod yaml file
touch pod.yml
chmod 777 pod.yml
ls

# edit pod definition
vim pod.yml

# view pod file
cat pod.yml

# create pod (imperative)
kubectl create -f pod.yml

# check pod status
kubectl get pods
kubectl get pods -o wide

# inspect pod
kubectl describe nginx
kubectl describe pod nginx

# check networking
ip addr
kubectl get pods -o wide

# delete pod
kubectl delete pod nginx

# recreate pod (declarative)
kubectl apply -f pod.yml

# verify pod again
kubectl get pods

# view command history
history
