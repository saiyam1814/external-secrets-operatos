# external-secrets-operatos

## Kubernetes cluster 
The first thing is a Kubernetes cluster that you need in order to do the demo 

## Vault installation 
```
kubectl create namespace vault
kubectl --namespace='vault' get all
helm repo add hashicorp https://helm.releases.hashicorp.com
helm search repo hashicorp/vault --versions
helm install vault hashicorp/vault --namespace vault --version 0.23.0
```

## Configure vault

Save the keys -> unseal vault -> enable the kv engine -> create the secret -> get the token to login to vault saved.


## Install external secrets operator

```
helm repo add external-secrets https://charts.external-secrets.io

helm install external-secrets \
   external-secrets/external-secrets \
    -n external-secrets \
    --create-namespace \
   --set installCRDs=true

```
## Create the secretstore and external secret
make sure to change the vault endpoint and token for your endpoint and you need to encode it as base64 before putting it in the file.
