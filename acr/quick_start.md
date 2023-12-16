# ACR Quick Start with az CLI

## Login into the subscription and create Resource Group : acr-rg

```bash
az login
az account set -s <subscription_name>
az account show -o table
az group list -o table 
az group create --name acr-rg --location westeurope
```

## Create ACR (SKU: Basic)

```bash
az acr list
az acr show --name <registry-name> --resource-group <RG_Name>
az acr show --name demoacr --resource-group acr-rg -o table 
```

az acr create --resource-group <resource_group_name> --name <new_registry_name> --sku Basic

Note: ACR name only alfa numeric charecter 

az acr create --resource-group acr-rg --name ocpdemoacr --sku Basic


Login to ACR and Push Images

Login Server: ocpdemoacr.azurecr.io

az acr show --name ocpdemoacr --resource-group acr-rg --output tsv --query loginServer
ocpdemoacr.azurecr.io




docker pull mcr.microsoft.com/hello-world
docker tag mcr.microsoft.com/hello-world ocpdemoacr.azurecr.io/hello-world:v1

docker push ocpdemoacr.azurecr.io/hello-world:v1
