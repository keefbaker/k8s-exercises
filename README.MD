# k8s-exercises

[![Pull Request Check](https://github.com/keefbaker/k8s-exercises/actions/workflows/validate.yml/badge.svg)](https://github.com/keefbaker/k8s-exercises/actions/workflows/validate.yml)

These exercises were created to help learn k8s for the team.

To start, create your namespace by running

```
kubectl create namespace <your-name>
```

Then set that to the one you're going to use by typing 

```
kubectl config set-context --current --namespace=<your-name>
```

Namespaces are a way to partially isolate an environment as when you interact with k8s using kubectl it will now interact using your new environment.

This allows names to be duplicated, because part of kube dns is the namespacing. so nginx.zaro.svc.cluster.local is different from nginx.sharad.svc.cluster.local.