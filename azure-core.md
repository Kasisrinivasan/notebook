
### Create Service Principal

```
 az ad sp create-for-rbac -n "<<service-principal-name>>"
```



### Display the Service Principal details

```
az ad sp list --filter "displayName eq '<<service-principal-name>>'"
```

### Reset Service principal

```
az ad sp credential reset --name "<<service-principal-name>>"
```
