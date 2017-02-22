# Multi-peer with CA

This needs at least 4 nodes to have Practical Byzantine Fault Tolerance (PBFT) working.

**NOTE: This is conflicting with our node-frontend at the moment.** I will fix this later this week.


### Computer Setup

... go path
... decoded go folder
... hyperledger go folder


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


### Check.

To SSH into one of the containers use with <CONTAINER-NAME> reflecting the container name

```bash
sudo docker exec -i -t <CONTAINER-NAME> /bin/bash
```

So in our case:

```bash
sudo docker exec -i -t multipeernoca_vp0_1 /bin/bash
```

Both the following commands should list the files for Hyperledger and our own blockchain:

```bash
ls -l /opt/gopath/src/github.com/hyperledger/fabric
ls -l /opt/gopath/src/github.com/DecodedCo/blockchain-golang-chaincode
```
