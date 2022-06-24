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
```
```
kubectl get svc my-cip-service
```
```
curl <CLUSTER-IP>:8080
```

