# blockchain-docker-compose

Docker files for the blockchain applications

First, clone this repo to your computer.

# Pull the docker containers

Make sure you have Docker running on your mac.

```
docker pull hyperledger/fabric-peer:latest
docker pull hyperledger/fabric-membersrvc:latest
```

### Documentation

* http://hyperledger-fabric.readthedocs.io/en/latest/Setup/Chaincode-setup/#running-the-chaincode

### Running 1 node + a membership service

Use the folder `one-peer-one-ca`. The first time start it up with:

```
docker-compose up
```

After the containers are created you can start using

```
docker-compose start
```

To stop the process, in a different shell run

```
docker-compose stop
```

This will stop the containers, but keep them around (see `docker ps -a`). To remove all containers:

```
docker rm -f $(docker ps -aq)
```


### Helpful Docker commands

1. View running containers:

```
docker ps
```

2. View all containers (active and non-active):

```
docker ps -a
```

3. Stop all Docker containers:

```
docker stop $(docker ps -a -q)
```

4. Remove all containers.  Adding the `-f` will issue a "force" removal:

```
docker rm -f $(docker ps -aq)
```

5. Remove all images:

```
docker rmi -f $(docker images -q)
```

6. Remove all images except for hyperledger/fabric-baseimage:

```
docker rmi $(docker images | grep -v 'hyperledger/fabric-baseimage:latest' | awk {'print $3'})
```

7. Start a container:

```
docker start <containerID>
```

8. Stop a containerID:

```
docker stop <containerID>
```

9. View network settings for a specific container:

 ```
docker inspect <containerID>
```

10. View logs for a specific containerID:

```
docker logs -f <containerID>
```
