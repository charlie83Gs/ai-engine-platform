https://docs.cilium.io/en/stable/installation/k8s-install-helm/


## Reinstall cluster roles and rolebindings

```bash
kubectl delete helmrelease -n cilium-system cilium-rlease
kubectl delete clusterrole cilium cilium-operator
kubectl delete ClusterRoleBinding cilium cilium-operator
```
