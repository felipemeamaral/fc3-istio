# Service Mesh with Istio

## Setup on k3d custer

### To be able to use istio, you have to create a kubernetes cluster

- We're going to use k3d as a tool to help to automate the process

```sh
brew install k3d
```

### Now you need to create the cluster itself

```sh
k3d cluster create -p "8000:30000@loadbalancer" --agents 2
```

### Install istioctl on Homebrew

```sh
brew install istioctl
```

### Install istio on Kubernetes cluster

```sh
istioctl install
```

Press Y to advance with the default installation.

### Install a new test deployment

````sh
kubectl apply -f deployment.yaml
````

### Set istio to set label on namespace default

```sh
kubectl label namespace default istio-injection=enabled
```

### Run a describe inside the new pod to istio being injected into it automatically

```sh
kubectl describe pods nginx[TAB]
```

### Install istio addons (Grafana, Jaeger, Kiali and Prometheus)

```sh
kubectl apply -f ADDON_NAME.yaml
```

### To see the dashboard run this command on Terminal

```sh
istioctl dashboard [grafana,jaeger,kiali,prometheus]
```

