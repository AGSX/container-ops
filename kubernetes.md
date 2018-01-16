Kubernetes
===

## Network Policies

By default, namespaces in Kubernetes do not have a network policy set, which means all pods in that namespace have unrestricted network access.

As a best practice, whenever a new namespace is created in Kubernetes, you should immediately create a default, “deny all” network policy.

```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny
spec:
  podSelector: {}
  policyTypes:
  - Ingress
  - Egress
```

Note that this means that pods that would normally be able to communicate with each other, or with other Kubernetes services, or fetch data from the Internet will not be able to do so until another network policy that specifically allows such traffic is created.