# Authenticate with ACR from AKS

## Configure ACR integration for existing AKS clusters
```
az aks update -n aksatin -g rgJuly21 --attach-acr atinregistryaks
```

## Import an image into your ACR
```
az acr import  -n atinregistryaks --source docker.io/library/nginx:latest --image nginx:v1
```

## Deploy the sample image from ACR to AKS
```
az aks get-credentials -g rgJuly21 -n aksatin
```

```
vim acr-nginx.yaml
```
### Content:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx0-deployment
  labels:
    app: nginx0-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx0
  template:
    metadata:
      labels:
        app: nginx0
    spec:
      containers:
      - name: nginx
        image: atinregistryaks.azurecr.io/nginx:v1
        ports:
        - containerPort: 80
```

## Apply yaml manifest
```
kubectl apply -f acr-nginx.yaml
kubectl get pods
```
