# Azure Kubernetes Commands

#### Installing AKS 
```
az aks install-cli
```

#### Creating  AKS cluster
```
  az aks create --resource-group rg-aks \
    --name aks-cluster \
    --location eastus \
    --kubernetes-version 1.15.7 \
    --generate-ssh-keys \
    --load-balancer-sku basic \
    --node-count 1 \
    --node-vm-size Standard_B2ms \
    --nodepool-name akspool  
```

----

#### Viewing the VM SKU's

```
  az vm list-skus -l eastus --size d2 -o table
```

----

#### Downloading the credentials

```
 az aks get-credentials --resource-group rg-aks --name aks-cluster
```

----
#### Retrieving the Public IP addess allocated to Ingress Controller
 
```
kubectl get svc  -n fend    ingress-nginx-ingress-controller -o jsonpath="{.status.loadBalancer.ingress[*].ip}"
```

## Other References
[https://github.com/Azure/aks-engine/tree/master/docs/topics](AKS Engine Topics)
