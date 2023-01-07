# Run docker as host

```
# Useful to run command as host user so output files are not root
docker run -it -u $(id -u ${USER}):$(id -g ${USER}) -v ["path-to-volume-mount"]:[/path-in-container] [docker-image] [cmd]
```
