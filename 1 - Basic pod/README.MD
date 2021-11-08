# Basic Pod

A pod is the smallest runnable item that exists in k8s. It consists of one or more containers and some basic instructions on how they should be run.

Pretty much everything in k8s is written in yaml.

# Exercise

change the *namespace* field on the pod to your name.

Apply the pod using:

```
kubectl apply -f basic-pod.yml
```

to check how it's doing run

```
kubectl get pods -n <your-name>
```
To see it working run:

```
kubectl port-forward nginx 8080:80 -n <your-name>
```

Then in your browser go to http://127.0.0.1:8080

Once the exercise is over and everyone is finished run

```
kubectl delete -f basic-pod.yml
```