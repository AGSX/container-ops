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
apiVersion: apps/v1beta2
kind: Deployment
metadata:
  name: nginx
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
      nodeSelector:
        env: dev
```
