# Elasticsearch sample

## prerequisites

- kubernetes cluster (probably need more than 2GB memory)


Ex. Kind

```
# you need more than 2GB memory.
kind create cluster
```

## start

```
# Install custom resource definitions
kubectl apply -f https://download.elastic.co/downloads/eck/1.0.1/all-in-one.yaml

# then, use kustomize
kubectl apply -k .
```

this sample use 'elastic' as namespace

Get login password.

```
PASSWORD=$(kubectl get secret quickstart-es-elastic-user -n elastic -o=jsonpath='{.data.elastic}' | base64 --decode)
```

From local machine,

```
curl -u "elastic:$PASSWORD" -k "https://localhost:9200"
```
