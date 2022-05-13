# Install the operator

Install the operator
```
kubectl apply -f https://raw.githubusercontent.com/mongodb/mongodb-atlas-kubernetes/main/deploy/all-in-one.yaml
```{{execute}}

Create your secrets
```
kubectl create secret generic mongodb-atlas-operator-api-key \
    --from-literal="orgId=<org>" \
    --from-literal="publicApiKey=<public>" \
    --from-literal="privateApiKey=<private>" \
    -n mongodb-atlas-system
kubectl label secret mongodb-atlas-operator-api-key atlas.mongodb.com/type=credentials -n mongodb-atlas-system
```

```
kubectl create secret generic atlaspassword --from-literal="password=mernk8s"
kubectl label secret atlaspassword atlas.mongodb.com/type=credentials
```{{execute}}

Create the project, cluster, and user
```
k apply -f ./mern-k8s/k8s/mdb_atlas.yaml
```{{execute}}

Test the connection string
```
kubectl get secret mern-k8s-db-admin-mern-k8s-user -o json | jq -r '.data | with_entries(.value |= @base64d)'
```{{execute}}