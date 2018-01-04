Docker Image Security
===

## Public Image Vetting

While most popular, public Docker images are communally vetted, in a security critical enterprise context it would be best to internally inspect, audit and vet, then republish all images privately \(see [The Docker Registry](./the-docker-registry.md)\).

To do this

1. Take any given public Docker image (note the specific tag) intended for use, e.g. `wordpress:4.9`.
2. Navigate to the Docker Hub image page, in this case [https://hub.docker.com/_/wordpress/](https://hub.docker.com/_/wordpress/)
3. Look for the specific tag in the description. There should a link to that image's Dockerfile. In this case, the original Dockerfile for `wordpress:4.9` can be found [here](https://github.com/docker-library/wordpress/blob/6a085d90853b8baffadbd3f0a41d6814a2513c11/php7.2/apache/Dockerfile)

We should now be able to inspect that Dockerfile and see exactly what commands were used to build that given image.

More importantly, we now can do two things.:

We can find the image `FROM` which this image was built on. In this case, it's `php:7.2-apache`.

We can keep following the same steps above to inspect and audit the entire Docker image lineage:

* [wordpress:4.9](https://github.com/docker-library/wordpress/blob/6a085d90853b8baffadbd3f0a41d6814a2513c11/php7.2/apache/Dockerfile)
* [php:7.2-apache](https://github.com/docker-library/php/blob/32313ea407379d70259e14414ec8aa0311c0a4c4/7.2/stretch/apache/Dockerfile)
* [debian:stretch-slim](https://github.com/debuerreotype/docker-debian-artifacts/blob/6af0f6159c515601731d92972a245199337e3ca6/stretch/slim/Dockerfile) (base)

Secondly, we can _recreate_ every intermediate image from source ourselves. Which means we can also inspect, audit, scan for vulnerabilities _all_ binaries and files that go into any given image. More importantly, we can build _and_ sign e.g. `internal/debian:strech-slim`, and by requiring enterprise users use _only_ the internally vetted and signed image, have greater confidence in the security of our production images.

## Docker Content Trust

Enable Docker Content Trust

```
export DOCKER_CONTENT_TRUST=1
```

