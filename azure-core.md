c
### Create Service Principal Subscription level scope

```
az login
az account set --subscription="${SUBSCRIPTION_ID}"
az ad sp create-for-rbac -n "<<service-principal-name>>" --role="Contributor" --scopes="/subscriptions/${SUBSCRIPTION_ID}"
```

### Create Resource group level scope

```
az login
az account set --subscription="${SUBSCRIPTION_ID}"
az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/${SUBSCRIPTION_ID}/resourceGroups/${RESOURCE_GROUP_NAME}"
```

### Display the Service Principal details

```
az ad sp list --filter "displayName eq '<<service-principal-name>>'" --query "[].{clientId:appId, tenant:appOwnerTenantId, objectId:objectId, password:password }"

```

### Reset Service principal

```
az ad sp credential reset --name "<<service-principal-name>>"
```
