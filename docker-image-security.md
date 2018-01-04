Docker Image Security
===

## Public Image Vetting

While most popular, public Docker images are communally vetted, in the interest of enterprise security it would be best to internally inspect, audit and vet, then republish (see [The Docker Registry](./the-docker-registry.md))

## Docker Content Trust

Enable Docker Content Trust

```
export DOCKER_CONTENT_TRUST=1
```

