Docker Image Security
===

## Public Image Vetting

While most popular, public Docker images are communally vetted, in a security critical enterprise context it would be best to internally inspect, audit and vet, then republish all images privately \(see [The Docker Registry](./the-docker-registry.md)\).

To do this

1. Take any given public Docker image (note the specific tag) intended for use, e.g. `wordpress:4.9`.
2. Navigate to the Docker Hub image page, in this case [https://hub.docker.com/_/wordpress/](https://hub.docker.com/_/wordpress/)
3. Look for the specific tag in the description. There should a link to that image's Dockerfile. In this case, the original Dockerfile for `wordpress:4.9` can be found [here](https://github.com/docker-library/wordpress/blob/6a085d90853b8baffadbd3f0a41d6814a2513c11/php7.2/apache/Dockerfile)
4. 

## Docker Content Trust

Enable Docker Content Trust

```
export DOCKER_CONTENT_TRUST=1
```

