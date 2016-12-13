# blockchain-docker-compose

Docker files for the blockchain applications

# Pull the docker containers

Make sure you have Docker running on your mac.

```
docker pull hyperledger/fabric-peer:latest
docker pull hyperledger/fabric-membersrvc:latest
```

### Documentation

* http://hyperledger-fabric.readthedocs.io/en/latest/Setup/Chaincode-setup/#running-the-chaincode

### Running 1 node + a membership service

The first time start it up with:

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

This will stop the containers, but keep them around (see `docker ps -a`). The volume's will be lost (so all stored data).


### Docker Tutorial

To come...