# Introduction
> The main goal is to build a Docker image of the project and publish it on Docker Hub, so we can use it to create a kubernetes deployment that we will expose using minikube tunnel.
# Steps

## Clone repo
```console
git clone <repo-url>
```

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