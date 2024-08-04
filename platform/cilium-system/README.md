https://docs.cilium.io/en/stable/installation/k8s-install-helm/
https://docs.cilium.io/en/stable/helm-reference/


# Initial install
```bash
cilium install --helm-auto-gen-values helm-values.yaml
```

## Reinstall cluster roles and rolebindings

```bash
kubectl delete helmrelease -n cilium-system cilium-release
kubectl delete clusterrole cilium cilium-operator
kubectl delete ClusterRoleBinding cilium cilium-operator
```
