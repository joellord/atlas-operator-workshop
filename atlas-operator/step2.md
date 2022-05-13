# Deploy the application

Deploy the back end 
```
kubect apply -f ./mern-k8s/k8s/back/service.yaml
kubect apply -f ./mern-k8s/k8s/back/deployment.yaml
```{{execute}}

Edit the BASE_URL parameter in _k8s/front/deployment.yaml_

Deploy the front end 
```
kubect apply -f ./mern-k8s/k8s/front
```{{execute}}

Deploy the ingress
```
kubectl apply -f ./mern-k8s/k8s/minikube_ingress.yaml
```{{execute}}