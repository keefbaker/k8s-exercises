# k8s-exercises

These exercises were created to help learn k8s for a client.

To start, create your namespace by running

```
kubectl create namespace <your-name>
```

Then set that to the one you're going to use by typing 

```
kubectl config set-context --current --namespace=<your-name>
```