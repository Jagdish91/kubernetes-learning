# Kubernetes Learning – Minikube & kubectl 

---

## Environment

- Windows with WSL2 (Ubuntu)
- Architecture: amd64
- Container Runtime: Docker Desktop
- Kubernetes: Minikube
- CLI: kubectl

---

## Complete Command History

# check system architecture and OS
uname -m


# download minikube (official)
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64

# install minikube
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64

# verify minikube binary
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

# create pod definition
vim pod.yml

# create pod (imperative)
kubectl create -f pod.yml

# check pod status
kubectl get pods
kubectl get pods -o wide

# inspect pod
kubectl describe pod nginx

# check networking
kubectl get pods -o wide

# delete pod
kubectl delete pod nginx

# view command history
history
