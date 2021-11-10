# Service

Now we have a way to run containers and to scale containers we need a way for the outside world to communicate with them. This is where services come into play

First look at the deployment, you will see this is the same as before.

apply it using:

```
kubectl apply -f deployment.yml
```

Now we will need to change some things in the service.yml

Change YOURNAME.DOMAIN to <yourname>.<the domain i send you in chat>. As this is a global DNS record, this needs to be unique, hence why your name

Change CERTIFICATE_ARN to the certificate arn I send you in chat.

Now apply the service

```
kubectl apply -f service.yml
```

As this has to bring up an AWS loadbalancer and Route53 DNS record and our VPN can be slow to update DNS this will take a few minutes.

To see the status run:

```
kubectl describe service nginx
```

This will also show you the loadbalancer name.

In a few minutes browse to *https://<your domain>* and you should see the nginx start page with full https.

This is because of the annotations.

destroying when done:

```
kubectl delete -f service.yml; kubectl delete -f deployment.yml
```
This will take some time as the service has to ensure the DNS record and loadbalancer are destroyed.