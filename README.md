# ImageOps Tutorial

## ArgoCD

install ArgoCD

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/
helm install argo-cd charts/argo-cd/
```

Access ArgoCD Web UI

```
kubectl port-forward svc/argo-cd-argocd-server 8080:443
kubectl get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Setup ArgoCD Application

```
helm template apps/ | kubectl apply -f -
```

## Setup Application

```
kubectl apply -k overlays/${ENV}
```
