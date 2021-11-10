# Helm

Helm is described as 'yum for kubernetes'. That's partly right, but it's also a bit like ansible for Kubernetes.

It allows you to install services easily and customize them

First we need to install the jenkins helm repo, to do this run:

```
helm repo add jenkins https://charts.jenkins.io
helm repo update
```

Helm charts have a value file that you can examine to show you what can be changed/updated. To look at this you can run:

```
helm show values jenkins/jenkins > values.yml
```

Then open the value file and skim through it to see what's possible

Now open jenkins.yml and change YOURNAME.DOMAIN to <yourname>.<the domain i sent in chat>

Let's install it

```
helm install <yourname> -f jenkins.yml jenkins/jenkins
```

It will take a few minutes for the containers to come up and for the DNS record/loadbalancer to propagate, but when they do, check on your jenkins by browsing to http://<yourname>.<the domain i sent in chat>

Once you're done clean up with

```
helm uninstall <yourname>
```
