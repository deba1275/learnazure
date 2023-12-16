### ACR Quick Start with az CLI

#### Login into the subscription and create Resource Group : acr-rg

```bash
az login
az account set -s <subscription_name>
az account show -o table
az group list -o table 
az group create --name acr-rg --location westeurope
```

#### Create ACR (SKU: Basic)

#### List the existing ACR and view details required.

```bash
az acr list
az acr show --name <registry-name> --resource-group <RG_Name>
az acr show --name demoacr --resource-group acr-rg -o table 
```

#### Create a new ACR into the RG acr-rg

```bash
az acr create --resource-group <resource_group_name> --name <new_registry_name> --sku Basic
```

<b>Note:</b> ACR name only accespt alfa numeric charecters and limit berween 5 to 55 length.

```bash
az acr create --resource-group acr-rg --name demoacr --sku Basic

To Check: az acr list -o table
```

#### Login to ACR and Push Images

Get the Login Server name
-  Login Server: ocpdemoacr.azurecr.io
```bash
$ az acr show --name ocpdemoacr --resource-group acr-rg --output tsv --query loginServer
ocpdemoacr.azurecr.io
$
```

Docker daemon must be running to test this steps

```bash
az acr login --name <registry_name>
$ az acr login -n demoacr
Login Sucessful
$
```

docker pull mcr.microsoft.com/hello-world
docker tag mcr.microsoft.com/hello-world ocpdemoacr.azurecr.io/hello-world:v1

docker push ocpdemoacr.azurecr.io/hello-world:v1
