# DOCKER
docker build -f .\Dockerfile -t lukasslizik/hellokubernetes:1.0 .
docker build -f .\Dockerfile -t lukasslizik/hellokubernetes:2.0 .

docker run -p 18081:8080 -d lukasslizik/hellokubernetes:1.0
docker run -p 18082:8080 -d lukasslizik/hellokubernetes:2.0

docker push lukasslizik/hellokubernetes:1.0
docker push lukasslizik/hellokubernetes:2.0

# MINIKUBE
minikube delete
minikube start --vm-driver hyperv

# KUBECTL
kubectl apply -f .\pods\firstPod.yaml
kubectl get pods
kubectl describe pod hello-kubernetes
kubectl apply -f .\services\loadBalancer.yaml
kubectl delete pod hello-kubernetes

kubectl apply -f .\deployments\Deployment1.yaml
kubectl apply -f .\deployments\Deployment1.yaml

# rolling update
kubectl set image deployment/hello-kubernetes-deployment-1 hellokubernetes=lukasslizik/hellokubernetes:2.0 --record
kubectl rollout undo deployment/hello-kubernetes-deployment-1