# Kuberenetes-Google-Cloud
Clone Repo and configure GCP CLI [Instruction](https://cloud.google.com/sdk/docs/install)
``` 
source ~/.zshrc
```
```
gcloud init --console-only
```
Make sure that Google Kubernetes Engine API is already enabled on your default project
```
gcloud container clusters create
``` 
```
gcloud container clusters get-credentials <cluster-name eg. my-cluster> --zone us-central1-c --project <default Project ID>
```

Creating Service Type: ClusterIP
```
kubectl apply -f my-deployment.yaml
```
```
kubectl get pods
```
```
kubectl apply -f my-cip-service.yaml
kubectl get service my-cip-service --output yaml
kubectl get nodes --output wide
```
```
kubectl get svc my-cip-service
```
```
curl <CLUSTER-IP>:8080
```
Creating a Service of type NodePort:
```
kubectl apply -f my-deployment-50000.yaml
kubectl apply -f my-np-service.yaml
kubectl get service my-np-service --output yaml
```
Finding external IP address of Nodes in Cluster
```
curl http://localhost:<Node-Port eg.31483 >
```
Creating a Service of type LoadBalancer
```
kubectl apply -f my-deployment-50001.yaml
kubectl get pods
kubectl apply -f my-lb-service.yaml
kubectl get service my-lb-service --output yaml
curl lb-External-IP:60000
```
Manually exposing deployments
```
kubectl expose deployment my-deployment --name my-cip-service \
    --type ClusterIP --protocol TCP --port 80 --target-port 8080
```
```
kubectl expose deployment my-deployment-50000 --name my-np-service \
    --type NodePort --protocol TCP --port 80 --target-port 50000
```
```
kubectl expose deployment my-deployment-50001 --name my-lb-service \
    --type LoadBalancer --port 60000 --target-port 50001
```
Delete GKE cluster:
```
gcloud projects list
gcloud config set project <Project ID>
gcloud container clusters delete my-cluster --zone us-central1-c
