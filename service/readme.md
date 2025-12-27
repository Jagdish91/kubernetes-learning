Kubernetes Services with Minikube 🚀

🛠 Tools Used
Minikube
Docker
kubectl
Nginx (sample app)

📘 Why Kubernetes Needs Services
Pods in Kubernetes are: Ephemeral (can be recreated anytime)
Assigned dynamic IP addresses

➡️ Directly accessing Pods via IP is unreliable.
Services solve this problem by: Providing a stable virtual IP
Routing traffic to Pods using labels & selectors

🔖 Labels & Selectors 
Services do NOT track Pods by IP.
Instead:
Pods have labels: Services use selectors to find matching Pods

Example:
selector:
  app: nginx

If a Pod dies and a new one is created with the same label, the Service automatically routes traffic to the new Pod.

1️⃣ ClusterIP Service 
What is ClusterIP?
Exposes the service inside the cluster only
Not accessible from outside Kubernetes
Used for internal communication (frontend → backend)

➡️ Requires SSH into the cluster node

2️⃣ NodePort Service
Exposes the service on each node’s IP
Accessible externally via: <NodeIP>:<NodePort>

➡️ No SSH required
➡️ Accessible from host machine

🔁 Traffic Flow (NodePort)
Client
  ↓
Minikube Node IP : NodePort
  ↓
Service
  ↓
Pod (matched by labels)

