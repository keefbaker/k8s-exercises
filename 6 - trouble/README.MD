# Troubleshooting

First we'll install the helm chart povided

```
helm install broken -f jenkins.yml jenkins/jenkins
```

It will take a few minutes but you will eventually notice the jenkins isn't coming up. 
The clue will be that it now has a number of restarts eventually even getting to CrashLoopBackOff status

lets see if there are any logs in the previous jenkins container

```
kubectl logs broken-jenkins-0 -c jenkins --previous
```

If the jenkins didn't get to start you may see:

Error from server (BadRequest): previous terminated container "jenkins" in pod "broken-jenkins-0" not found

in which case it may be in Init:CrashLoopBackoff status.

If this is the case we need to check the init container

```
kubectl logs broken-jenkins-0 -c init --previous
```

Once we do this we can see in the logs there is no such plugin as dogmeat.

Remove dogmeat from the plugin list in jenkins.yml.

Then run

```
helm upgrade broken -f jenkins.yml jenkins/jenkins
kubectl delete pod broken-jenkins-0
```

After a little while jenkins should restart correctly

Once you're done clean up with

```
helm uninstall broken
```
