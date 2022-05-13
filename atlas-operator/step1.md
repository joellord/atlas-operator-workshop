# Set up the environment
Install the latest minikube version
`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
install minikube-linux-amd64 /usr/local/bin/minikube`{{execute}}

Delete the existing image, and start with the latest Kubernetes version
`minikube delete && minikube start --driver=none --kubernetes-version=v1.23.3 --host-dns-resolver=true --dns-proxy=false`{{execute}}

Enable the `ingress` addon
`minikube addons enable ingress`{{execute}}

Clone the repository
```
git clone https://github.com/joellord/mern-k8s.git
```{{execute}}