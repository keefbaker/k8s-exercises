# Basic Pod

A pod is the smallest runnable item that exists in k8s. It consists of one or more containers and some basic instructions on how they should be run.

Pretty much everything in k8s is written in yaml.

# Exercise

Apply the pod using:

```
kubectl apply -f basic-pod.yml
```

to check how it's doing run

```
kubectl get pods 
```

Let's check the logs:

```
kubectl logs nginx
```

To see it working run:

```
kubectl port-forward nginx 8080:80 
```

Then in your browser go to http://127.0.0.1:8080

Once the exercise is over and everyone is finished run

```
kubectl delete -f basic-pod.yml
```