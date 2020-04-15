# KubernetesPlayground
Kubernetes, Docker, Deployment

# Scripts
powershell as admin
	minikube start --vm-driver hyperv

# rolling update
kubectl set image deployment/hello-world1-deployment hello-world1=lukasslizik/hello-world2 --record
kubectl rollout undo deployment/hello-world1-deployment 

# Clusters, Nodes, Pods, Containers