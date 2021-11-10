# Storage

One way to create persistence in Kubernetes is to create a persistent volume. This volume will survive a pod being destroyed.

We have a storage controller, lets look at that

```
kubect get sc
```

So we don't need to manually create the persistent volume, we can just create the ticket to claim a volume and the storage controller will do the rest.

Create the volume

```
kubectl create -f volume.yml
```

Now create the deployment

```
kubectl create -f nginx.yml
```

After a while you should see 3 nginx pods when you run *kubectl get pods*. Lets connect to one.

```
kubectl exec --stdin --tty <pod name> -- /bin/sh
```

inside the pod run the following so we can confirm the volume is there and then put something in place to ensure the volume is the same across all three pods

```
df -h
cd /myvol
echo "hello" > hello.txt
ls
exit
```

choose a different pod and run:

```
kubectl exec --stdin --tty <pod name> -- /bin/sh
```

Inside the pod run the following to prove it's the same volume.

```
df -h
cd /myvol
ls
cat hello.txt
exit
```

Cleanup by running

```
kubectl delete -f nginx.yml
kubectl delete -f volume.yml
```
