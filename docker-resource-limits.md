Docker Resource Limits
====

Example

```
$ docker run -d \
    --name='low_prio' \
    --cpuset-cpus=0 \
    --cpu-shares=20 \
    busybox md5sum /dev/urandom
$ docker run -d \
    --name='high_prio' \
    --cpuset-cpus=0 \
    --cpu-shares=80 \
    busybox md5sum /dev/urandom
```

(Ref: https://www.cloudsigma.com/manage-docker-resources-with-cgroups/)
