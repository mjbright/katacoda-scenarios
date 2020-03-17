
# Scenario description

I this scenario we will look at implementing the Docker 'Cats/Dogs/ Voting app.

First, once your environment is created, we will check our nodes and then install the application sources

## Node setup

Check all nodes using command

`kubectl get nodes`{{copy}}

**Note**: In case only 1-node is currently working we will untaint that node

We can untaint all nodes using the command
`kubectl taint nodes node-role.kubernetes.io/master- --all`{{copy}}

## Getting voting app source code

`git clone https://github.com/dockersamples/example-voting-app`{{copy}}

`cd example-voting-app`{{copy}}



