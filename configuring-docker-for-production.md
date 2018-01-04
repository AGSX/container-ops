Configuring Docker for Production
===

## Logging

By default, Docker logging uses the JSON file driver and will store an unlimited amount of log messages, which can quickly consume all space on your Docker hosts.

As a precaution and best practice, set the Docker logging options to a certain maximum file size and number of files.

Edit or create `/etc/docker/daemon.json` and specify:

```
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m",
  }
}
```

That allows up to 100MB of logs per container. Adjust as appropriate given the number target of containers per host and the desired log retention.
