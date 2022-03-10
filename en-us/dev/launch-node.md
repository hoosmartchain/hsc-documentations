# Launch Node

## Recommand Hardware 

* testnet
```
8core
16g
ssd iops>5k
```

* mainnet
```
16core
32g
ssd iops>5k
```

## Recommand Port 
* testnet
```
8645  for http-rpc-api
8646  for ws-rpc-api
33668 for p2p
```

* mainnet
```
8545  for http-rpc-api
8546  for ws-rpc-api
32668 for p2p
```



## Launch testnet node

### Prepare node directory
* /home/ubuntu/hsc-testnet-node
```
mkdir /home/ubuntu/hsc-testnet-node
cd /home/ubuntu/hsc-testnet-node
mkdir data logs
touch config.toml
```

### Prepare configuration files

* copy info below to config.toml

```
[Eth]
SyncMode = "fast"
DiscoveryURLs = []
TrieCleanCacheRejournal= 300000000000

[Eth.Miner]
GasFloor = 8000000
GasCeil = 8000000
GasPrice = 0
Recommit = 3000000000
Noverify = false

[Eth.Ethash]
CacheDir = "ethash"
CachesInMem = 2
CachesOnDisk = 3
CachesLockMmap = false
DatasetDir = "/home/ubuntu/hsc-testnet-node/data/.ethash"
DatasetsInMem = 1
DatasetsOnDisk = 2
DatasetsLockMmap = false
PowMode = 0

[Eth.TxPool]
Locals = []
NoLocals = false
Journal = "transactions.rlp"
Rejournal = 3600000000000
PriceLimit = 1
PriceBump = 10
AccountSlots = 16
GlobalSlots = 4096
AccountQueue = 64
GlobalQueue = 1024
Lifetime = 10800000000000

[Node]
DataDir = "/home/ubuntu/hsc-testnet-node/data"
InsecureUnlockAllowed = true
NoUSB = true
IPCPath = "geth.ipc"
HTTPHost = "0.0.0.0"
HTTPPort = 8645
HTTPCors = ["*"]
HTTPVirtualHosts = ["*"]
HTTPModules = ['eth', 'net', 'web3']

WSHost = "0.0.0.0"
WSPort = 8646
WSModules = ['eth', 'net', 'web3']

GraphQLVirtualHosts = ["localhost"]


[Node.P2P]
MaxPeers = 50
NoDiscovery = false

StaticNodes=["enode://160ae2ec30b079ace074cfa28c73757f2493fd7afd807e0da901e68eff31ead944ff6eec7b854dfffffb1b4d4cc886829455e62f8422edd937694498544f9c40@13.230.35.234:33668","enode://d4718eb176c63c4752adeaf050df31b93a85de7e37e69b82fbe7a6f28f4e556c976a227250367a9e9ffd2e08b6d513448f7dff4969e4afaabb170b71eac2907b@35.73.127.28:33668","enode://bfe0bdaaeed5767f8a79204f18a45afc5a802eed6428b2c0aebf757f3a98276268090d5b6f1f839330f6b0cd397e22ad4f99affefd7a132421d43446c0a3f8a8@18.181.232.158:33668"]

ListenAddr = ":33668"
EnableMsgEvents = false

[Node.HTTPTimeouts]
ReadTimeout = 30000000000
WriteTimeout = 30000000000
IdleTimeout = 120000000000
```

use fast sync in the config by default, if full node is needed, change this line
```
SyncMode = "fast"
```
to
```
SyncMode = "full"
```

### Launch script


* testnet


```
#!/usr/bin/env bash
geth \
--testnet \
--config /home/ubuntu/hsc-testnet-node/config.toml  \
--logpath /home/ubuntu/hsc-testnet-node/logs \
--verbosity 3  >> /home/ubuntu/hsc-testnet-node/logs/systemd_chain_console.out 2>&1
```

for archive, add：

```
--syncmode full \
--gcmode archive \
```

which is：

```
#!/usr/bin/env bash
geth \
--testnet \
--config /home/ubuntu/hsc-testnet-node/config.toml  \
--logpath /home/ubuntu/hsc-testnet-node/logs \
--syncmode full \
--gcmode archive \
--verbosity 3  >> /home/ubuntu/hsc-testnet-node/logs/systemd_chain_console.out 2>&1
```