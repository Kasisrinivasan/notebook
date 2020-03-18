
### Verifying log agent collection setting 
``` bash
kubectl get pods -n 'kube-system'

kubectl logs -p 'omsagent-rs-<<replace_name>>' -n 'kube-system'

```
