# Deployment

A deployment combines a replicaset (a collection of X number of the same type of pod)
with a pod definition. A replicaset is like an autoscaling group.

Let's apply this:

```
kubectl apply -f deployment-basic.yml
```

Let's check the pods, deployment and the replicaset.

```
kubectl get pods
kubectl get deployment
kubectl get replicaset
```

Notice that the replicaset takes the name of the deployment with an identifier, and the pod starts with the replicaset name but then has an identifier after that.

Try deleting the pod

```
kubectl delete pod <pod name>
```

What happens?

Now scale the deployment

```
kubectl scale --replicas=5 deployment/nginx
```

Now run

```
kubectl get pods
```

You can see that it has scaled up.

Let's try scaling the replicaset itself

```
kubectl get replicaset # to get the replicaset name
kubectl scale --replicas=7 rs/<replicaset name>
```

If you use *kubectl get pods* and *kubectl describe replicaset <replicaset name>* you may have seen the pods appear and disappear.

This is because a replicaset inside a deployment is managed by the deployment, so the setting the deployment has takes precedence.

After you're done clean up.

```
kubectl delete -f deployment-basic.yml
```