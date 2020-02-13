
#### Build the container image from the Dockerfile
```
az acr build --registry $ACR_NAME --image helloacrtasks:v1 .
```

#### Verify that the image has been created and stored in the registry.
```
az acr repository list --name $ACR_NAME --output table
```



#### Enable the registry admin account on Container registry
```
az acr update -n $ACR_NAME --admin-enabled true
```

#### To retrieve the username and password for the admin account 
```
az acr credential show --name $ACR_NAME
```

#### Get the ACR login server name 
```
az acr list --resource-group myResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```
