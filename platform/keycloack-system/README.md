https://artifacthub.io/packages/helm/bitnami/keycloak

## Creating a sealed secret

**Create a secret yaml file using kubectl dryrun**

```bash
kubectl -n default create secret generic keycloack -n keycloack-system  \
--from-literal=password=changeme123! \
--dry-run=client \
-o yaml > secretname.yaml

kubeseal --fetch-cert \
--controller-name=sealed-secrets-controller \
--controller-namespace=sealed-secrets-system \
> pub-sealed-secrets.pem

kubeseal --format=yaml --cert=pub-sealed-secrets.pem --namespace keycloack-system\
< secretname.yaml > keycloack-sealed.yaml

rm secretname.yaml pub-sealed-secrets.pem
```

## Accesing the service locally

```bash
kubectl port-forward -n keycloack-system service/keycloack-keycloak 8000:80
```

```bash
kubectl port-forward -n keycloack-system pods/keycloack-keycloak-0 9000:9000
```
