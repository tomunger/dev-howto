#


# Container Registry

[Howto](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-get-started-portal?tabs=azure-cli)

Create a registry.  You are given a domain name ending in `azurecr.io`.  

Tag your image for the registry with `docker tag`.

Push the image.


    ACR_NAME=tumtumregistry
    RES_GROUP=site-tumtum

    az container create \
        --resource-group $RES_GROUP \
        --name tumtum-files \
        --image $ACR_NAME.azurecr.io/tumtum-files-amd64:1.0.0 \
        --registry-login-server $ACR_NAME.azurecr.io \
        --registry-username $(az keyvault secret show --vault-name $AKV_NAME --name $ACR_NAME-pull-usr --query value -o tsv) \
        --registry-password $(az keyvault secret show --vault-name $AKV_NAME --name $ACR_NAME-pull-pwd --query value -o tsv) \
        --dns-name-label acr-tasks-$ACR_NAME \
        --query "{FQDN:ipAddress.fqdn}" \
        --output table

        HAc=aditoB7O

# Execute in a container

    az container exec -g site-tumtum --name tumtum-files --exec-command "/bin/bash"

