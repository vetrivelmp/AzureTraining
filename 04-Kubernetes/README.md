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
az account set --subscription "0aebf870-9dad-42d6-b841-71391fa04322"
sudo az aks get-credentials --resource-group LnTKubernetes --name atingupta2005-cluster
```
```
sudo kubectl config use-context atingupta2005-cluster
sudo kubectl create namespace "ns-atingupta2005"  # Note: Specify your namespace here.
sudo kubectl get namespaces
sudo kubectl config set-context --current --namespace="ns-atingupta2005"  # Note: Specify your namespace here.
sudo kubectl get nodes
```

### Login to ubuntu where Docker is installed and run:
```
sudo docker run -d -p 8080:8080 atingupta2005/hello-world-rest-api:0.0.1.RELEASE
docker ps
```

- Visit <publicIP>:8080/hello-world

### 1.-------Deploy Docker image in Kubernetes
```
sudo kubectl create deployment hello-world-rest-api --image=atingupta2005/hello-world-rest-api:0.0.1.RELEASE
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

- To get details about the artifact
```
sudo kubectl explain pods
```

- Get more details of the pod
```
sudo kubectl describe pod hello-world-rest-api-58ff5dd898-9trh2
```

```
sudo kubectl get pods
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

### 3.------Replicaset
```
kubectl get replicasets
```

- Since we are telling that how much replicas we need, a replicaset will take care of it.
```
kubectl scale deployment hello-world-rest-api --replicas=4
kubectl get pods
kubectl get replicaset
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get rs -o wide
```

- Lets delete one Pod and see how its auto created. Please note that use correct Pod ID
```
kubectl delete pod hello-world-rest-api-67c79fd44f-n6c7l
kubectl get pods -o wide
kubectl delete pod hello-world-rest-api-67c79fd44f-8bhdt
kubectl get pods -o wide
```

### 4.------------Deployment
- Deployment ensures the release upgrades without any issue.
- We don’t want to have the downtime while release upgrade and Deployment plays a key role in achieving that
- There are many deployment strategies - Rolling Update
- Whenever we want to deploy new release of our existing application, we desire zero downtime
- If we change the image and that image is not existing, it will not deploy that
```
kubectl set image deployment hello-world-rest-api hello-world-rest-api=DUMMY_IMAGE:TEST
```

```
kubectl get service
```

- Now if we check in browser the old version is still running
- If we check our replicasets, then there are 2 replicasets. One with old image, other for error image
```
kubectl get rs -o wide
```

- We will see that there are 4 Pods, 3 are for old image, and new one has invalid status
```
kubectl get pods
```
