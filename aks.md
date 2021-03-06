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

#### configuring kubectl tool to manage the cluster.
```console
az aks get-credentials --resource-group $name-rgp --name $name
```
Validate the cluster
```console
kubectl cluster-info
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

### Querying the Deployments, services, pod 

```
kubectl get deploy,rs,po,svc,ingress -n namespacename
```

----
#### Create a Service object that exposes the deployment
```
kubectl expose deployment hello-world --type=LoadBalancer --name=my-service
```

----
#### Kubernetes dashboard
-- kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml
```
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```
Retrieving the secrets
```
kubectl -n kubernetes-dashboard get secret
kubectl -n kube-system get services
```
Opening the dashboard
```console
az aks browse -n aks-demo  -g  rg-aks-demo
```

#### Interacting with the Pod/Container 
```
kubectl exec podname  -n namespacename  -i -t   -- bash -il
```

#### Mounting Azure File share
```
sudo mount -t cifs -o dir_mode=0777,file_mode=0777,uid=1000,gid=1000,username=XXXXX,password=XXXXXX=,vers=3.0 //westeuropeqamutu.file.core.windows.net/agrial-magento-media /var/lib/kubelet/pods/7628a8e8-e348-11e8-9daa-4603d9f6b58b/volumes/kubernetes.io~azure-file/agrial-magento-media
```

## Other References
[https://github.com/Azure/aks-engine/tree/master/docs/topics](AKS Engine Topics)
