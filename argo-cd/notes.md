## Architecture of argo-cd and its components

click here: [official docs](https://argo-cd.readthedocs.io/en/stable/operator-manual/architecture/)

## Argo-cd installation using helm

Helm chart: https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd

- Go to the release page and find the stable release Non HA setup

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.16/manifests/install.yaml
```

### References

Tech world with nana: [video](https://www.youtube.com/watch?v=MeU5_k9ssrs)
