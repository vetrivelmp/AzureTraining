# Kubernetes

## Install KubeCTL
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

- Install Azure CLI (If Required)
```
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

- Setup autocomplete in bash into the current shell, bash-completion package should be installed first.
```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanently to your bash shell.
```

- Use these commands if Azure Cluster and your namespace is already created
```
az login
#az account set --subscription "0aebf870-9dad-42d6-b841-71391fa04322"
sudo az aks get-credentials --resource-group rgJune21 --name kubercluster1
```
```
sudo kubectl config use-context kubercluster1
sudo kubectl create namespace "ns-atingupta2005"  # Note: Specify your namespace here.
sudo kubectl get namespaces
sudo kubectl config set-context --current --namespace="ns-atingupta2005"  # Note: Specify your namespace here.
sudo kubectl get nodes
```
### 1.-------Deploy Docker image in Kubernetes
```
sudo kubectl create deployment hello-world-rest-api --image=atingupta2005/hello-world-rest-api:0.0.1.RELEASE
sudo kubectl get deployments
sudo kubectl expose deployment hello-world-rest-api --type=LoadBalancer --port=8080
sudo kubectl get service
sudo kubectl get pods
sudo kubectl scale deployment hello-world-rest-api --replicas=3
sudo kubectl get pods
```

### 2.--------Pods
- Pod is the smallest deployable unit. Can not have container without Pod. Container lives inside Pod
```
sudo kubectl get pods
sudo kubectl get pods -o wide
```

```
sudo kubectl delete pod hello-world-rest-api-58ff5dd898-62l9d
```

```
sudo kubectl get pods
```

- Get list of various artifacts
```
sudo kubectl get all
sudo kubectl get events
sudo kubectl get pods
sudo kubectl get replicaset
sudo kubectl get deployment
sudo kubectl get service
```
