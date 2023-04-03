## Build image
```console
docker build -t <dockerID>/website-nginx:1.0.0 .
```

## Publish image on Docker Hub

```console
docker push <dockerID>/website-nginx:1.0.0
```

## Create deployement

```console
kubectl create deployment website-deployment --image <dockerID>/website-nginx:1.0.0
```

## Create service

```console
kubectl expose deployment/website-deployment --type LoadBalancer --port 80
```

## Expose Service with minikube

```console
minikube service website-deployment
```

## Scale the application

```console
kubectl scale deployment/website-deployment --replicas 6
```