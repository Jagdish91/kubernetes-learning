Kubernetes Basics with Minikube 🚀

This project documents my hands-on learning journey with Kubernetes using Minikube (Docker driver).
The goal is to understand core Kubernetes objects by actually creating, deleting, and observing them in action.

🛠 Tools Used

Minikube (local Kubernetes cluster)

Docker (Minikube driver)

kubectl (Kubernetes CLI)

Nginx (sample application)

📘 Core Concepts Learned
1️⃣ What is a Container?

A container is a lightweight, standalone package that includes:

Application code
Runtime
Libraries
Dependencies

➡️ Containers are not managed directly by Kubernetes.

2️⃣ What is a Pod?

A Pod is the smallest deployable unit in Kubernetes.
A pod can contain one or more containers

Containers in a pod:
Share the same network (IP & port space)
Share storage (volumes)

➡️ Pods are ephemeral — if deleted, they are gone unless managed by a higher object.

3️⃣ What is a ReplicaSet?

A ReplicaSet ensures that a specified number of pod replicas are running at all times.
If a pod dies → ReplicaSet creates a new one
Maintains desired state

Example:
kubectl get replicaset
kubectl get rs


➡️ You usually don’t create ReplicaSets directly.

4️⃣ What is a Deployment?

A Deployment is a higher-level abstraction that manages:
Pods
ReplicaSets
Rolling updates
Scaling
Auto-healing

Example:
kubectl apply -f deployment.yml
kubectl get deployments
kubectl get pods


If you delete a pod manually:
kubectl delete pod <pod-name>


Kubernetes automatically recreates it 🎯
This demonstrates self-healing.

🔁 Relationship Between Objects
Deployment
   ↓
ReplicaSet
   ↓
Pod
   ↓
Container


You define a Deployment
Deployment manages a ReplicaSet
ReplicaSet manages Pods
Pods run Containers

🧪 Commands Practiced
minikube start --driver=docker

kubectl get pods
kubectl get deployments
kubectl get all

kubectl apply -f deployment.yml

kubectl delete pod nginx
kubectl get pods -w

🧠 Key Learnings
Kubernetes works on declarative configuration
You define what you want, not how to do it
Kubernetes constantly reconciles actual state vs desired state
Auto-healing and scalability are built-in, not add-ons
