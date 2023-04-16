## Architecture of argo-cd and its components

click here: [official docs](https://argo-cd.readthedocs.io/en/stable/operator-manual/architecture/)

## Argo-cd installation using helm

Helm chart: https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd

- By default, argo-cd server service will be cluser ip, create a Ingress rule to expose it or NodePort

- Ingress rule to expose argo-cd:

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  annotations:
    alb.ingress.kubernetes.io/certificate-arn: <arn>
    alb.ingress.kubernetes.io/listen-ports: '[{"HTTP":80,"HTTPS":443}]'
    alb.ingress.kubernetes.io/scheme: internet-facing
    alb.ingress.kubernetes.io/target-type: ip
    kubernetes.io/ingress.class: alb
spec:
  rules:
  - host: argocd.bmaddi.ot-xecm.com
    http:
      paths:
      - backend:
          service:
            name: argocd-server
            port:
              number: 443
        path: /
        pathType: Prefix
```

**Note:** You will run into some issue, solution [here](https://github.com/argoproj/argo-cd/issues/2953)

- Go to the release page and find the stable release Non HA setup

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.16/manifests/install.yaml
```

### References

Tech world with nana: [video](https://www.youtube.com/watch?v=MeU5_k9ssrs)
