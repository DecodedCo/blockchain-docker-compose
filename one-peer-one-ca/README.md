### Starting/Stopping the containers

Make sure your `$GOPATH` is correctly configured and you have pulled to repo according to standards.

```
docker-compose build
docker-compose up
```

To stop

```
docker-compose stop; docker rm -f $(docker ps -aq);
```

The last command is to delete all volumes.