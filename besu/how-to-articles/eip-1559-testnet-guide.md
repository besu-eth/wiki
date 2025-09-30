# EIP-1559 testnet guide

Instructions to join the EIP-1559 testnet for the first time. 

## Step-by-step guide

1. Select an EIP-1559 capable Ethereum Client, the current available clients are:
  1. Hyperledger Besu on [master](https://github.com/hyperledger/besu) branch
  2. Nethermind on [eip1559](https://github.com/NethermindEth/nethermind/tree/eip1559) branch
  3. Geth (soon) on [1559\_test\_fixCalcBaseFee](https://github.com/n0cte/go-ethereum/tree/1559_test_fixCalcBaseFee) branch 
2. Download the genesis file depending on the client selected at step 1
  1. Hyperledger Besu [genesis](https://github.com/ConsenSys/eip1559-testnet/blob/master/config/besu/genesis.json)
  2. Other clients TBA
3. Download the config file template depending on the client selected at step 1
  1. Hyperledger Besu [sample config file](https://github.com/ConsenSys/eip1559-testnet/blob/master/config/besu/config.toml)
4. (Optional) Add information to be listed in the block explorer (ask for credentials in the [#1559-fee-market Discord server](https://discord.gg/B4yx9SQ))
5. Run the Ethereum Client with the proper configuration.  
You will likely need to manually add peers ([Besu instructions](https://besu.hyperledger.org/en/stable/Reference/API-Methods/#admin_addpeer)) to connect to. Here is a list of nodes that are running on the testnet: 

```
enode://0c72e2b7873e4342d725b5990c17adb2b159aad2ff5853de7e4910b25522a1f9e78f9cd802a8a3225b8fae4e994e522b50d6bd5a163eb3a7b49a0a73ca9a1c7e@13.236.147.35:30303

enode://1c6d296749018e4e4a78baf9a8a3048aae2557c3f2f11a340570d57e71071e2e9816a5f5d9215a333d12b432a81ff5017520b09461c4a102e72c7a1a2d9d7d0f@18.222.108.145:30303

enode://3eca270e124b5e24e846bb39d0a911d152cfd2671be079478e72e768363c959852301b40b2afffddbe45a285fd752fa4541e8376f73dad688757e0a07a35e164@15.188.238.162:30303
```

## Interacting with the testnet 

Since wallet providers don't support yet EIP-1559 style transactions, we have implemented [a toolbox](http://eip1559-tx.ops.pegasys.tech/) to interact with the testnet. It provides the following features:

- A form UI to send both legacy and 1559-style transactions to the testnet;
- A form UI to query the testnet's \`BASE FEE\`;
- Links to the testnet [block explorer](http://eip1559-testnet.ops.pegasys.tech:3000/) & [ethstats page](http://eip1559-testnet.ops.pegasys.tech:3001/);
- Links to the EIP-1559 [spec](https://eips.ethereum.org/EIPS/eip-1559) & [updates](https://hackmd.io/@timbeiko/1559-updates/);

The tool can also be installed locally. The instructions are available [here](https://github.com/abdelhamidbakhta/eip1559-ui).

**`Warning: Use only test private keys when interacting with the testnet!`**