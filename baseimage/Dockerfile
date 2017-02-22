FROM hyperledger/fabric-peer

# Pull the right version of Hyperledger-fabric. This is publicly available.
RUN cd .. && \
		rm -rf fabric && \
		git clone https://github.com/hyperledger/fabric && \
		cd fabric && \
		git checkout v0.6 && \
		git pull
		
# Get Decoded chaincode and build it
RUN go get github.com/DecodedCo/blockchain-marketplace-chaincode && \
		cd /opt/gopath/src/github.com/DecodedCo/blockchain-marketplace-chaincode && \
		go build .

RUN go get github.com/DecodedCo/blockchain-ballot-chaincode && \
		cd /opt/gopath/src/github.com/DecodedCo/blockchain-ballot-chaincode && \
		go build .
