# How to replay from a snapshot

### Mainnet Snapshot VexChain 

pull update snapshot from 
```console
https://v2.vexascan.com/snapshots
```

### example configurate replay from snapshot
#### create bash file 

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
--p2p-peer-address explorer.vexanium.com:8091 \
--p2p-peer-address 188.166.233.69:8092 \
--p2p-peer-address 209.97.162.124:8091 \
--p2p-peer-address 34.81.37.55:9010 \
>> "nodeos.log" 2>&1 & \
echo $! > $DATADIR"/eosd.pid"
```

