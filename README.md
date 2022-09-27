# How to replay from a snapshot

### Mainnet Snapshot VexChain 
```console
wget https://github.com/genesisblockid/snapshot/releases/download/v2.1.0/snapshots.tar
```

### example configurate replay from snapshot

```bash
#!/bin/bash
DATADIR="./data"

if [ ! -d $DATADIR ]; then
  mkdir -p $DATADIR;
fi

nodeos \
--snapshot ./path/snapshotfile.bin \
--signature-provider VEX7h7......=KEY:5KGA.... \
--plugin eosio::producer_plugin \
--plugin eosio::producer_api_plugin \
--plugin eosio::chain_plugin \
--plugin eosio::chain_api_plugin \
--plugin eosio::state_history_plugin \
--plugin eosio::http_plugin \
--plugin eosio::history_api_plugin \
--plugin eosio::history_plugin \
--data-dir $DATADIR \
--blocks-dir $DATADIR"/blocks" \
--config-dir $DATADIR \
--producer-name producer_account \
--http-server-address 0.0.0.0:8443 \
--p2p-listen-endpoint 0.0.0.0:9010 \
--chain-state-db-size-mb 20480 \
--access-control-allow-origin=* \
--access-control-allow-headers 'content-type' \
--contracts-console \
--disable-replay-opts \
--http-validate-host=false \
--verbose-http-errors \
--enable-stale-production \
--p2p-peer-address  explorer.vexanium.com:8091 \
--p2p-peer-address 188.166.233.69:8092 \
--p2p-peer-address 139.180.136.160:9090 \
--p2p-peer-address 167.179.103.141:9090 \
--p2p-peer-address 178.128.217.200:9090 \
--p2p-peer-address 178.128.217.200:9090 \
--p2p-peer-address 45.32.122.5:9095 \
--p2p-peer-address 159.65.142.132:8080 \
--p2p-peer-address 139.180.192.207:8092 \
--p2p-peer-address 209.97.162.124:8091 \
--p2p-peer-address 34.81.37.55:9010 \
>> "nodeos.log" 2>&1 & \
echo $! > $DATADIR"/eosd.pid"
```

