FROM hyperledger/fabric-peer
# make sure we have v0.6 of fabric
RUN cd .. && \
		rm -rf fabric && \
		git clone https://github.com/hyperledger/fabric && \
		cd fabric && \
		git checkout v0.6 && \
		git pull
# get Decoded chaincode and build it
RUN go get github.com/DecodedCo/blockchain-vote/golang-chaincode && \
		cd /opt/gopath/src/github.com/DecodedCo/blockchain-vote/golang-chaincode && \
		go build .
