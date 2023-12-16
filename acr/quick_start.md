
Login into the subscription and create Resource Group : acr-rg

az login
az account set -s <subscription_name>
 az account show -o table
az group list -o table 
az group create --name acr-rg --location westeurope

Create ACR (SKU: Basic)

az acr list
az acr show --name <registry-name> --resource-group <RG_Name>
Ex.
az acr show --name vccicpregistry2 --resource-group icp-registry -o table 

az acr create --resource-group <resource_group_name> --name <new_registry_name> --sku Basic

Note: ACR name only alfa numeric charecter 

az acr create --resource-group acr-rg --name ocpdemoacr --sku Basic


Login to ACR and Push Images

Login Server: ocpdemoacr.azurecr.io

dbiswas [ ~ ]$ az acr show --name ocpdemoacr --resource-group acr-rg --output tsv --query loginServer
ocpdemoacr.azurecr.io
dbiswas [ ~ ]$ 



docker pull mcr.microsoft.com/hello-world
docker tag mcr.microsoft.com/hello-world ocpdemoacr.azurecr.io/hello-world:v1

docker push ocpdemoacr.azurecr.io/hello-world:v1 ![image](https://github.com/deba1275/learnazure/assets/140979881/d9c82444-e324-401a-8524-b81a46af6b37)
