#### Enabling Pod policies

* Run the below command to Register pod security policy feature preview
```
az feature register --name PodSecurityPolicyPreview --namespace Microsoft.ContainerService
```
* Enable pod security policy on an AKS cluster
```
az aks update \
    --resource-group rg-aks-demo \
    --name aks-cf-demo-eus \
    --enable-pod-security-policy
```

#### Viewing AKS Pod Security policies
To view the policies available

```
kubectl get psp
```

### Installing & Uninstalling OPA Gatekeeper

kubectl apply -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper/master/deploy/gatekeeper.yaml

kubectl delete -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper/master/deploy/gatekeeper.yaml


### K8 working with Constraints 
```
kubectl get constrainttemplates
kubectl delete  constrainttemplates 'k8srequiredlabels"
```

```
kubectl delete -f constraints
kubectl delete -f templates
```



