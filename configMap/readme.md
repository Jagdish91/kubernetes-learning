Kubernetes ConfigMap with Nginx (Env + Volume Mount)

This repository demonstrates how to use a Kubernetes ConfigMap with an nginx Deployment to manage configuration without rebuilding images or repeatedly redeploying applications.
The setup also integrates:

🎯 Objective
Store configuration in a ConfigMap
Read values as environment variables
Mount configuration files using volumes
Update configuration without rebuilding images
Understand how ConfigMaps fit into real Kubernetes workflows

🧠 Key Concepts Learned
ConfigMaps decouple configuration from application code
Environment variables can be injected from ConfigMaps
ConfigMaps can be mounted as files using volumes
Application configuration can be changed without recreating images


📁 Files in This Setup
File	Purpose
depolyment.yml	nginx Deployment
config-map.yml	ConfigMap for nginx configuration

🧪 Useful Commands Used
kubectl get cm
kubectl describe cm
kubectl apply -f config-map.yml
kubectl exec -it deploy/nginx-deployment -- /bin/sh
kubectl edit service nginx-app-service
kubectl get ingress
kubectl get pods

