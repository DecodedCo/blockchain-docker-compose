# CURL requests

### Registering/Deploying the Chaincode

Documentation for HyperLedger CLI is [here](https://github.com/hyperledger/fabric/blob/master/docs/protocol-spec.md#6313-chaincode-deploy)

```bash
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -H "Postman-Token: 74a9cd60-8c61-c0c4-ac0d-39ca203285dd" -d '{
    "jsonrpc": "2.0", 
    "method": "deploy",  
    "params": {
        "type":1, 
        "chaincodeID": {
            "name": "DecodedBlockChain",
            "path": "github.com/DecodedCo/blockchain-marketplace-chaincode"
        }, 
        "ctorMsg": { 
            "function":"init", 
            "args": [] 
        } 
    },
    "id": 0
}' "http://0.0.0.0:7050/chaincode" | python -m json.tool
```

The deploy will give you an `ID` that becomes the new `chaincodeID` name.

Reponse will look like

```javascript
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   539  100   190  100   349      6     12  0:00:31  0:00:28  0:00:03     0
{
    "id": 0,
    "jsonrpc": "2.0",
    "result": {
        "message": "7d6ec9fcfb252983e39cb49817fe754f3f421a74beafe6056a3776b7a10b829a10b9e5b2dbd056e17cbc1b05716bd5a7d87e4ff3c3ad0c241b7a3de54fd03ae5",
        "status": "OK"
    }
}
```

```
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "jsonrpc": "2.0", 
    "method": "query",  
    "params": {
        "type":1, 
        "chaincodeID": {
            "name":"7d6ec9fcfb252983e39cb49817fe754f3f421a74beafe6056a3776b7a10b829a10b9e5b2dbd056e17cbc1b05716bd5a7d87e4ff3c3ad0c241b7a3de54fd03ae5"
        }, 
        "ctorMsg": { 
            "function":"read", 
            "args": [ "Owners" ] 
        } 
    },
    "id": 1337
}' "http://0.0.0.0:7050/chaincode" | python -m json.tool
```

```
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "jsonrpc": "2.0", 
    "method": "query",  
    "params": {
        "type":1, 
        "chaincodeID": {
            "name":"7d6ec9fcfb252983e39cb49817fe754f3f421a74beafe6056a3776b7a10b829a10b9e5b2dbd056e17cbc1b05716bd5a7d87e4ff3c3ad0c241b7a3de54fd03ae5"
        }, 
        "ctorMsg": { 
            "function":"readAll", 
            "args": [ ] 
        } 
    },
    "id": 1337
}' "http://0.0.0.0:7050/chaincode" | python -m json.tool
```

Return something like:

```javascript
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   537  100   149  100   388   8656  22541 --:--:-- --:--:-- --:--:-- 22823
{
    "id": 1337,
    "jsonrpc": "2.0",
    "result": {
        "message": "{\"Assets\":null,\"Owners\":null,\"PendingTransactions\":null,\"Transactions\":null}",
        "status": "OK"
    }
}
```

### Security Disabled

Security is disabled on all nodes for now.

```bash
curl http://0.0.0.0:7050/network/peers | python -m json.tool
```

```javascript
{
  "peers": [
    {
      "ID": {
        "name": "vp3"
      },
      "address": "172.17.0.4:7051",
      "type": 1
    },
    {
      "ID": {
        "name": "vp2"
      },
      "address": "172.17.0.5:7051",
      "type": 1
    },
    {
      "ID": {
        "name": "vp1"
      },
      "address": "172.17.0.6:7051",
      "type": 1
    },
    {
      "ID": {
        "name": "vp0"
      },
      "address": "172.17.0.3:7051",
      "type": 1
    }
  ]
}
```

### Security Enabled.

```bash
curl http://0.0.0.0:7050/network/peers | python -m json.tool
```

```javascript
{
  "peers": [
    {
      "ID": {
        "name": "vp1"
      },
      "address": "172.17.0.4:7051",
      "type": 1,
      "pkiID": "joEOyoOOMZwd8TcD7TmPodbUgRd1yox9JuadjHVAqSs="
    },
    {
      "ID": {
        "name": "vp2"
      },
      "address": "172.17.0.5:7051",
      "type": 1,
      "pkiID": "g51RMtKBITUO7Xaa9c+iI6S0dOp12smqz10zmCCOXzA="
    },
    {
      "ID": {
        "name": "vp3"
      },
      "address": "172.17.0.6:7051",
      "type": 1,
      "pkiID": "h+JxBz948VhwfbDJFjTERsV2/EmDAVHAEjy0LaVYDdM="
    },
    {
      "ID": {
        "name": "vp0"
      },
      "address": "172.17.0.3:7051",
      "type": 1,
      "pkiID": "o/xR3+4WEP6sgz1i/rlN/4K630xn70icNxYNZv/xDqQ="
    }
  ]
}
```
