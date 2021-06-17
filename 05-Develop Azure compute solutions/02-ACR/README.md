# Azure Pipelines Using ACR

## Understand how ACR and ACI works
### Create  ACR Manually
1. Create Azure Container Registry using Azure Portal named - appregistry1000atin

### Create Docker Image and upload image to ACR
1. Run the commands on Linux Machine Docker
```
sudo az login

// Login into your Azure container registry
// Change the registry name
sudo az acr login --name appregistry1000atin

// Tag your image
// Change the registry name
sudo docker tag dotnetapp appregistry1000atin.azurecr.io/dotnetapp

// Then push the image onto Azure container registry
// Change the registry name
sudo docker push appregistry1000atin.azurecr.io/dotnetapp
```

### Create ACI using the Image uploaded to ACR
1. Open Azure Portal\Container Registry\My ACR\Registries and Refresh
1. Open ACR\Access Keys and enable Admin user option
1. Create Azure Resource - Azure Container Instance. Chose Image Source -> ACR
1. Chose ACR, Image and tag
1. Networking Tab -> Public, Port 80
1. Grab Public IP of ACI and open on browser
1. Open ACI\Containers. Inspect Events, Properties, Logs
