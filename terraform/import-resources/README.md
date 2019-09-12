# Import resources for a static site into Terraform

Write up the Terraform resources for pre-existing Azure resources and import them into the state.

## Setup (AVADO)

Login and set the subscription:

```console
$ az login
$ az account set --subscription 'AVADO Dev Sandbox'
```

Create the resources:

```console
$ az group create --name sre-interview --location ukwest
$ az storage account create --resource-group sre-interview --name avadosreintvwcorp \
        --sku Standard_LRS --kind StorageV2 --access-tier cool --https-only true
$ az storage blob service-properties update --account-name avadosreintvwcorp \
        --static-website --404-document 404.html --index-document index.html
$ az storage account keys list --account-name avadosreintvwcorp
$ az storage blob upload --account-name avadosreintvwcorp --auth-mode key \
        --container-name '$web' --name index.html --file index.html
$ az storage account show --name avadosreintvwcorp
```

Pop a copy of `terraform` into this directory and make sure it's executable, then initialise the state:

```console
$ ./terraform init
$ ./terraform plan
```

## Teardown

Destroy the resources:

```console
$ az group delete --name sre-interview
```
