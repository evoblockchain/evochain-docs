# Join the Public Testnet With Docker
## Run EVO testnet fullnode with docker

### 1. Download the docker image

```
docker pull okevochain/fullnode-testnet:latest
```

### 2. Set the data directory


Download the testnet snapshot from [here](../resources/snapshot.html), and unzip it into a data directory ${DATA_DIR}.



### 3. Run docker container
```
docker run -d --name evochain-testnet-fullnode -v ${DATA_DIR}:/root/.evochaind/data/ -p 8545:8545 okevochain/fullnode-testnet:latest
```
`Notice: ${DATA_DIR} has to be an absolute path`


### 4. View the running log
```
docker logs --tail 100 -f evochain-testnet-fullnode
```

### 5. Stop and restart the fullnode
- Stop
```
docker stop evochain-testnet-fullnode
```
- Restart
```
docker start evochain-testnet-fullnode
```

### 5. RPC
When docker gets to the latest block, local RPC can be used：`http://localhost:8545`
