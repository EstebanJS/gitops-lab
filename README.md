# Helm chart de NGINX

Chart Helm propio para desplegar NGINX en Kubernetes.

## Requisitos

- Kubernetes 1.23+
- Helm 3+

## Instalar

Desarrollo:

```sh
helm upgrade --install nginx ./charts/nginx \
  --namespace nginx-dev \
  --create-namespace \
  -f ./charts/nginx/values-dev.yaml
```

Producción:

```sh
helm upgrade --install nginx ./charts/nginx \
  --namespace nginx-prod \
  --create-namespace \
  -f ./charts/nginx/values-prod.yaml
```

Los valores específicos de entorno sobrescriben los valores comunes de `values.yaml`.
Para validar el chart antes de instalarlo:

```sh
helm lint ./charts/nginx
helm template nginx ./charts/nginx -f ./charts/nginx/values-dev.yaml
helm template nginx ./charts/nginx -f ./charts/nginx/values-prod.yaml
```
