# Shandong Testnet

NOTE: Shandong has been **retired**. Here's the announcement

> We have decided to deprecate Shandong following an exchange with [@TimBeiko](https://twitter.com/TimBeiko?ref_src=twsrc%5Etfw), [@vdWijden](https://twitter.com/vdWijden?ref_src=twsrc%5Etfw) (Geth), [@parithosh\_j](https://twitter.com/parithosh_j?ref_src=twsrc%5Etfw) (DevOps) and [@elbuenmayini](https://twitter.com/elbuenmayini?ref_src=twsrc%5Etfw) (Testing) on devnet alignment.  
>   
> What do we have and what will follow as devnets for Shanghai, Withdrawals, EOF and Sharding?  
>   
> A 🧵:
> 
> — Former EF JavaScript Team (@EFJavaScript) [December 1, 2022](https://twitter.com/EFJavaScript/status/1598323497939378180?ref_src=twsrc%5Etfw)

  

This testnet adds support for

- [EIP-3540](https://eips.ethereum.org/EIPS/eip-3540): EOF - EVM Object Format v1
- [EIP-3651](https://eips.ethereum.org/EIPS/eip-3651): Warm COINBASE
- [EIP-3670](https://eips.ethereum.org/EIPS/eip-3670): Code Validation
- [EIP-3855](https://eips.ethereum.org/EIPS/eip-3855): PUSH0 instruction
- [EIP-3860](https://eips.ethereum.org/EIPS/eip-3860): Limit and meter initcode

## Running clients

### Consensus client

As an after merge network, a consensus client is required. For running on [Consensys' Teku](https://github.com/ConsenSys/teku) you can follow the instructions bellow

- Download [config.yaml](https://raw.githubusercontent.com/ethereumjs/consensus-deployment-ansible/master/shandong-testnet/custom_config_data/config.yaml) from [ethereumjs](https://github.com/ethereumjs/) repository
- Start Teku with the following parameters

```
--initial-state=[https://raw.githubusercontent.com/ethereumjs/consensus-deployment-ansible/master/shandong-testnet/custom_config_data/genesis.ssz](https://raw.githubusercontent.com/ethereumjs/consensus-deployment-ansible/master/shandong-testnet/custom_config_data/genesis.ssz)  
--network=[location of config.yaml]  
--data-base-path=[consensus data directory]  
--data-storage-mode=archive  
--ee-endpoint=[http://localhost:8551](http://localhost:8551)  
--p2p-discovery-bootnodes=enr:-LK4QHkdCND7lcPwqP0oP8EvjtyEIEwlufo4Q2WLU7lfnE7wXaiPFYqrxG2ve0yjwobsv-JivPPnPgM5FXF9_AUe2JIGh2F0dG5ldHOIAAAAAAAAAACEZXRoMpA6j89cITN5Av__________gmlkgnY0gmlwhC5lfi2Jc2VjcDI1NmsxoQO2iyKHl53XEZpkmqwzrNde8tJtHBG1juKX6GQ8maqYAIN0Y3CCIyiDdWRwgiMo,enr:-LK4QFUme0A5wcehaAVkgo3wILst__VwT-CS90IAHRf81EEDewxXYOY3tGH0kYg8jm3dRap-ebt9W2YpYxK4RhICoc4Gh2F0dG5ldHOIAAAAAAAAAACEZXRoMpA6j89cITN5Av__________gmlkgnY0gmlwhLKAy_OJc2VjcDI1NmsxoQIioMWqai_HMbtalAFqTa97lLgjfA_D9NBt9BenWmKjDIN0Y3CCIyiDdWRwgiMo,enr:-LK4QClQvVrrQ9Jm0mOUX8I9vu-anp-dgD9FSiW8Ep0uR6pEZh4t8iMljhXnE2q1UjL2rHAJeIxlrdbwcn1wjeLaamwGh2F0dG5ldHOIAAAAAAAAAACEZXRoMpA6j89cITN5Av__________gmlkgnY0gmlwhI5draqJc2VjcDI1NmsxoQKZ1U-C4IWnkiu6EvbIls9iRazxW5RZej-htHgwNf3Ef4N0Y3CCIyiDdWRwgiMo,enr:-LK4QGMlUKIzZVYqB2uIsizLIaKrPlHrGyZFCg5ond0soaGGOdsV9oR_50PAnOTE_6GZN6p_uqqkvGtnXPyhKEiizbYGh2F0dG5ldHOIAAAAAAAAAACEZXRoMpA6j89cITN5Av__________gmlkgnY0gmlwhKRcrjiJc2VjcDI1NmsxoQIO0t2j7TMxczat4kjQJaFikgg3mNCMQmgUX99zotTV5YN0Y3CCIyiDdWRwgiMo
```

### Execution client

Besu has support for *Shandong* testnet integrated on the **main** branch, so you only need to set `--network=shandong` and then you can define any of the existing [CLI options](https://besu.hyperledger.org/en/stable/public-networks/reference/cli/options/) as you need. E.g.

```
--network=shandong  
--sync-mode=FULL  
--data-path=[execution data directory]  
--rpc-http-enabled=true  
--engine-rpc-enabled=true  
--engine-jwt-disabled=true  
--rpc-http-api=ADMIN,DEBUG,ETH,NET,WEB3
```

## Development

Besu is able to stay in sync with Shandong(\*)

### Implemented EIPs

- EIP-3540: [PR#4644](https://github.com/hyperledger/besu/pull/4644)
- EIP-3651: [PR#4620](https://github.com/hyperledger/besu/pull/4620)
- EIP-3670: [PR#4644](https://github.com/hyperledger/besu/pull/4644)
- EIP-3855: [PR#4660](https://github.com/hyperledger/besu/pull/4660)
- EIP-3860: [PR#4726 (pending)](https://github.com/hyperledger/besu/pull/4726)

(\*): including PR [#4711](https://github.com/hyperledger/besu/pull/4711) and solving [#4740](https://github.com/hyperledger/besu/issues/4740)  

## Other resources

- [Block explorer](https://explorer.shandong.ethdevops.io)
- #shandong-testnet @ [EthereumJS' Discord server](https://discord.gg/TNwARpR)
- [Shandong Management Meta Issue](https://github.com/ethereumjs/ethereumjs-monorepo/issues/2375) @ ethereumjs repository