# Dockerize Dot Net app

Note: We have build a simple Dot Not Project and zipped the published folder and copied to GitHub. We will directly download it on Linux VM

## Steps
```
mkdir core-web-app-docker
cd core-web-app-docker
wget https://github.com/atingupta2005/Azure-Devops-AZ-400/raw/master/Module-19-Managing-Containers-using-Docker/1-Dockerize-Dot-Net-app/core-web-app-docker.zip
unzip core-web-app-docker.zip
rm core-web-app-docker.zip
#Create/Download our Docker file in the directory copied to linux vm - refer [Dockerfile](Dockerfile)
wget https://raw.githubusercontent.com/atingupta2005/Azure-Devops-AZ-400/master/Module-19-Managing-Containers-using-Docker/1-Dockerize-Dot-Net-app/Dockerfile
#Build image
sudo docker build -t dotnetapp .
#Create container
sudo docker run -d -p 80:80 dotnetapp
```

- Check the browser for your app
```
curl localhost
```


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
1. To connect to container, click on Connect
1. All files are there in /app inside container
```
ls /app
```
