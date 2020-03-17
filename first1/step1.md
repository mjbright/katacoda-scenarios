
# Scenario description

I this scenario we will look at implementing the Docker 'Cats/Dogs/ Voting app.

First, once your environment is created, we will check our nodes and then install the application sources

## Node setup

Check all nodes using command

```sh
kubectl get nodes
```

**Note**: In case only 1-node is currently working we will untaint that node

We can untaint all nodes using the command
```sh
kubectl taint nodes node-role.kubernetes.io/master- --all
```

## Getting voting app source code

```bash
git clone https://github.com/dockersamples/example-voting-app

cd example-voting-app
```



