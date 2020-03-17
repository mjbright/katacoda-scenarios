
# Starting the Voting App

`kubectl create -f kube-deployment.yml`{{copy}}

# Checking the App

Now check that the application is running correctly.

**Note**: We will just look at the Deployments initially


List the running deployments using the command:
`kubectl get deploy`{{copy}}

You should see output, something like:
```

NAME     READY   UP-TO-DATE   AVAILABLE   AGE
db       1/1     1            1           2m3s
redis    1/1     1            1           2m3s
result   1/1     1            1           2m2s
vote     2/2     2            2           2m2s
worker   0/1     1            0           2m1s
```

**Note**: The "*READY*" colu In the above example

```
NAME     READY   UP-TO-DATE   AVAILABLE   AGE
db       1/1     1            1           24m
redis    1/1     1            1           24m
result   1/1     1            1           24m
vote     2/2     2            2           24m
worker   1/1     1            1           24m
```

