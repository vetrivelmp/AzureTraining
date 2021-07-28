# Terraform-Kubernetes-Deployment
## Create AKS cluster using Terraform

- Refer:
    - https://github.com/atingupta2005/azure-devops-sample-pipelines/tree/05-azure-kubernetes-cluster-iaac-pipeline


### Review the files in GitHub Repo
  - Review files for Kubernetes cluster
    - /configuration/iaac/azure/kubernetes

###  Setup Client ID, Secret and Public Key
  - Connect to the Virtual VM
  - Install Azure CLI
    ```
    Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
    ```
  - Connect to Azure Portal
    ```
    az login
    ```
  - Copy the Subscription ID from the output of above command
  - Create Service Principal
    ```
    az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/<subscription-id>"
    ```

  - Save these credentials securely
  - Create SSH Public Key
    ```
    ssh-keygen -m PEM -t rsa -b 4096 -f azure_rsa
    ```

### Create DevOps Pipeline to deploy AKS
- Create service connection
  - Open Project Settings\Service Connections
  - Click - New Service connection
     - Name: azure-resource-manager-service-connection
     - Type: Azure Resource Manager
     - Service principal (manual)

- Install Terraform Plugins
    - https://marketplace.visualstudio.com/items?itemName=charleszipp.azure-pipelines-tasks-terraform
    - https://marketplace.visualstudio.com/items?itemName=ms-devlabs.custom-terraform-tasks
- Create a new pipeline and refer the code from:
    - https://github.com/atingupta2005/azure-devops-sample-pipelines/blob/05-azure-kubernetes-cluster-iaac-pipeline/05-azure-kubernetes-cluster-iaac-pipeline.yml
- Modify pipeline to change the references to:
    - Service Connections (If required)
    - Unique Storage account name in Backend configuration
- Edit Pipeline and click "Variables" to create Environment Variables:
    - client_id
    - client_secret
- Create file to store public key
    - From left menu open section - "Library" in new TAB
    - Click on tab - "Secure files"
    - Click button "+Secure file"
    - Upload the public key
- Run the pipeline
- Verify that the AKS is ready in Azure Portal

## Deploy Builds as Microservices to Kubernetes
- Create a Service Connection to Kubernetes Cluster
    -  Name: azure-kubernetes-connection
    -  Namespace: Default
-  Create new pipeline using
    -  Repo: https://github.com/atingupta2005/azure-devops-sample-pipelines
    -  Branch: 06-azure-kubernetes-code-ci-cd-pipeline
-  Refer deployment.yml which contains all the configuration to deploy our container to K8S cluster
-  Create a Service connection to Docker Hub
    -  Name: atingupta2005-docker-hub
- 
-  
