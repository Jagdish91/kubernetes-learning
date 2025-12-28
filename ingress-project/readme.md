Kubernetes Ingress with Minikube (Hands-On Implementation)

This repository demonstrates a complete end-to-end Kubernetes networking flow using:

Deployment
Service (NodePort → ClusterIP)
Ingress (nginx ingress controller)
Minikube (Docker driver)

The goal of this project was to deeply understand how traffic flows from outside the cluster to a container, and how Ingress, Service ports, and Pod ports interact.

🧠 What I Learned
How Services route traffic using labels & selectors, not IPs
Difference between:
containerPort
targetPort
service port
nodePort

How to troubleshoot broken connectivity by changing ports intentionally

How Minikube exposes Ingress using the nginx ingress controller

🏗 Architecture & Traffic Flow
Client (Browser / curl)
        |
        |  http://first-nginx.example
        v
Ingress Controller (nginx)
        |
        |  host + path rules
        v
Service (web / nginx-app-service)
        |
        |  port: 8080
        v
Pod
        |
        |  targetPort → containerPort
        v
nginx container (port 80)


Key concept:

Ingress → Service port → Service targetPort → Pod containerPort

📁 Files in this Repository
File	Purpose
deployment.yml	Deploys nginx application
service.yml	Exposes pods via Service
ingress-example.yml	Routes HTTP traffic via Ingress
🚀 Step-by-Step Implementation
1️⃣ Start Minikube
minikube start --driver=docker

2️⃣ Create Deployment (nginx)
kubectl apply -f deployment.yml
kubectl get deployments
kubectl get pods -o wide

nginx container listens on port 80

Pods are labeled so Services can discover them

3️⃣ Create Service

Initially tested with NodePort to understand external access:

kubectl apply -f service.yml
kubectl get service
minikube ip
curl <minikube-ip>:30007


Later switched to ClusterIP, which is the correct backend for Ingress.

4️⃣ Enable Ingress Addon (Minikube)
minikube addons enable ingress
kubectl get pods -n ingress-nginx
kubectl get ingressclass


This installs the nginx ingress controller inside the cluster.

5️⃣ Create Ingress Resource
kubectl apply -f ingress-example.yml
kubectl get ingress


Ingress routes traffic based on:

Host

Path

6️⃣ Configure Local DNS (hosts file)
sudo vim /etc/hosts


Add:

<ingress-ip> first-nginx.example

7️⃣ Access the Application
curl http://first-nginx.example


🎉 Traffic now flows through Ingress → Service → Pod



Key takeaways:
Services abstract Pod IPs
Ingress never talks directly to Pods
service.port ≠ targetPort
NodePort is not required for Ingress backends
Ingress controller is the real entry point
