Kubernetes
===

## Node segregation

To segregate workloads, e.g. "UAT" and "Dev" so they don't share physical nodes:

1. Label the nodes

```
# First list all your nodes
kubectl get nodes

# Next, label a particular node:
# kubectl label nodes <node-name> <label-key>=<label-value>
kubectl label nodes node0 env=dev
```

2. Use `nodeSelector` in your deployments

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    env: dev
spec:
  containers:
  - name: nginx
    image: nginx
  nodeSelector:
    env: dev
```
