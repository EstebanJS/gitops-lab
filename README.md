# gitops-lab

Repo de práctica de GitOps con Helm y Argo CD.

```
charts/mi-app/          Chart Helm de la app (nginx)
  values.yaml           Valores por defecto
  values-dev.yaml       Lo que cambia en dev
  values-prod.yaml      Lo que cambia en prod
  templates/            Deployment y Service
argocd/apps/            Definiciones de Application de Argo CD
```

## Probar el chart localmente

```sh
helm template mi-app ./charts/mi-app -f ./charts/mi-app/values-dev.yaml
helm template mi-app ./charts/mi-app -f ./charts/mi-app/values-prod.yaml
```

## Desplegar con Argo CD

1. Sube este repo a GitHub/GitLab y cambia `repoURL` en `argocd/apps/mi-app-dev.yaml`.
2. Aplica la Application:

```sh
kubectl apply -f argocd/apps/mi-app-dev.yaml
```

Argo CD sincroniza el chart con `values-dev.yaml` en el namespace `mi-app-dev`.
