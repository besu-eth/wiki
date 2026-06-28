# Devnet Testing and Tooling

The following is a guide for running as much internal testing as possible prior to an Ethereum devnet. The examples below are for the Pectra hardfork, you will need to replace those assets with ones relevant to the hardfork network being tested.

## Kurtosis

*Useful for small local interops*

- Assertor tests, for example Pectra devnets were at [https://raw.githubusercontent.com/ethpandaops/assertoor/refs/heads/master/playbooks/pectra-dev/kurtosis/all.yaml](https://raw.githubusercontent.com/ethpandaops/assertoor/refs/heads/master/playbooks/pectra-dev/kurtosis/all.yaml)
- Setup [https://github.com/ethpandaops/ethereum-package](https://github.com/ethpandaops/ethereum-package)
- Create a yml file, e.g. `besu-teku.yml`

```yaml
participants_matrix:
  el:
    - el_type: besu
      el_image: hyperledger/besu:develop
  cl:
    - cl_type: teku
      cl_image: consensys/teku:develop

network_params:
  electra_fork_epoch: 1
  min_validator_withdrawability_delay: 1
  shard_committee_period: 1
  churn_limit_quotient: 16
additional_services:
  - dora
  - spamoor_blob
  - tx_spammer
  - assertoor
dora_params:
  image: "ethpandaops/dora:master-latest"
snooper_enabled: true
spamoor_blob_params:
  throughput: 10
  max_blobs: 2
  max_pending: 40
assertoor_params:
  image: "ethpandaops/assertoor:master"
  tests:
    - file: https://raw.githubusercontent.com/ethpandaops/assertoor/refs/heads/master/playbooks/pectra-dev/kurtosis/all.yaml
  
```

Then run with:

```bash
kurtosis run --enclave besu-teku github.com/ethpandaops/ethereum-package --args-file besu-teku.yml
kurtosis web
```

Useful commands

```bash
kurtosis engine start
kurtosis engine stop
kurtosis enclave ls
kurtosis enclave dump
kurtosis enclave rm besu-teku --force
kurtosis service logs besu-teku snooper-engine-1-teku-besu
```

## Hive

- eest/consume-engine, eest/consume-rlp [https://hive.ethpandaops.io/pectra/index.html](https://hive.ethpandaops.io/pectra/index.html#summary-sort=name)
- rpc-compat, graphql etc [https://hivetests2.ethdevops.io/](https://hivetests2.ethdevops.io/)
- [~~https://hivetests.ethdevops.io/~~](https://hivetests.ethdevops.io/)
- [~~https://hive.pectra-devnet-5.ethpandaops.io/](https://hive.pectra-devnet-5.ethpandaops.io/)~~ [https://hive.ethpandaops.io/pectra-devnet-6/index.html#summary-sort=name](https://hive.ethpandaops.io/pectra-devnet-6/index.html#summary-sort=name)
- To run [https://github.com/ethereum/hive](https://github.com/ethereum/hive) locally:
    - `git clone git@github.com:ethereum/hive.git; cd hive`
    - `go build .`
    - `cd cmd/hiveview; go build .`
    - `./hive --sim rpc-compat --client besu`
    - View results: `./cmd/hiveview/hiveview -serve`

### Hive Repo GHA

If you want the definitive command for the entire simulator run, you can check the command executed by the corresponding github action here:

[https://github.com/ethpandaops/pectra-devnets/actions/runs/13900015592#summary-38889248399](https://github.com/ethpandaops/pectra-devnets/actions/runs/13900015592#summary-38889248399)

The client config is also available.

### EEST via hive

`./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file=besu-main.yaml --sim.buildarg fixtures=https://github.com/ethereum/execution-spec-tests/releases/download/pectra-devnet-6%40v1.0.0/fixtures_pectra-devnet-6.tar.gz --client.checktimelimit=60s --sim.parallelism=4 -sim.limit '.*fork_CancunToPrague or fork_Prague.*'`

```yaml
- client: besu
  nametag: hyperledger_besu_main
  dockerfile: git
  build_args:
    github: hyperledger/besu
    tag: main
```

### Limit to an EIP / test

 e.g. EIP2935…
`./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file="./besu-main.yaml" --sim.buildarg fixtures=[https://github.com/ethereum/execution-spec-tests/releases/download/pectra-devnet-6%40v1.0.0/fixtures_pectra-devnet-6.tar.gz](https://github.com/ethereum/execution-spec-tests/releases/download/pectra-devnet-5%40v1.3.0/fixtures_pectra-devnet-5.tar.gz) --client.checktimelimit=60s --sim.parallelism=4 -sim.limit ".*tests/prague/eip2935.*"` 

e.g. Limit to a specific test and enable besu TRACE logging:

`./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file="./besu-local.yaml" --sim.buildarg fixtures=http://github.com/ethereum/execution-spec-tests/releases/download/v4.1.0/fixtures_develop.tar.gz --client.checktimelimit=60s --sim.parallelism=4 -sim.limit ".*tests/prague/eip7702_set_code_tx/test_set_code_txs.py::test_set_code_multiple_valid_authorization_tuples_first_invalid_same_signer.*" -docker.output --sim.loglevel 5`

### Config file - example for testing a branch fix

```yaml
- client: besu
  nametag: matkt-fix-code-delegation-issue-wo-clear-eip7685
  dockerfile: git
  build_args:
    github: matkt/besu
    tag: fix-code-delegation-issue-wo-clear
```

If you want to test local changes, in besu build the docker image locally with:
`./gradlew distDocker` 
and update your client file like so, using the appropriate commit hash from your locally built image (check with `docker image ls hyperledger/besu | head`).

```yaml
- client: besu
  nametag: besu-local
  build_args:
    baseimage: hyperledger/besu
    tag: 25.1-develop-701d413
```

Karim’s fix via the gradle reference tests:

[https://github.com/hyperledger/besu/pull/8197](https://github.com/hyperledger/besu/pull/8197)

### Running hive 

```bash
sudo apt install -y golang
git clone https://github.com/ethereum/hive
cd hive
go build .
```

`time sudo ./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file="./besu.yaml" --sim.buildarg fixtures=http://github.com/ethereum/execution-spec-tests/releases/download/v4.1.0/fixtures_develop.tar.gz --client.checktimelimit=60s --sim.parallelism=18 -sim.limit '.*fork_Prague.*'`

## EEST (aka execution-spec-tests)

### Run using execution-spec-tests

- Follow instructions for [https://github.com/ethereum/execution-spec-tests](https://github.com/ethereum/execution-spec-tests)
- Run tests and fill using besu’s evmtool runner `uv run fill -k eip7702 --fork=Prague --evm-bin=../besu/build/install/besu/bin/evmtool --evm-dump-dir=./besu-dump/7702`
    - This ends up using `T8nExecutor.runTest` as the runner (for both state and blockchain tests?)
    - For debugging you can find a `t8n.sh` for each test in the dump directory
        - 1. `BESU_OPTS=-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 evmtool t8n-server`
        - 2. `./t8n.sh`
- Run tests and fill using EELS (this is how they generate the test artifacts in [https://github.com/ethereum/execution-spec-tests/releases](https://github.com/ethereum/execution-spec-tests/releases)
`uv run fill -k eip7702 --fork=Prague --evm-dump-dir=./eels-dump/7702` 

`uv run fill -k "test_call_types[fork_Prague-state_test-inf_pair-call_opcode_STATICCALL-]" --fork=Prague --evm-dump-dir=./dump tests/prague`

### Run via gradle referenceTests (requires pre or full release)

- Note the branch/tag name and artifact name from [https://github.com/ethereum/execution-spec-tests/releases](https://github.com/ethereum/execution-spec-tests/releases)
- Update `ethereum/referencetests/build.gradle` with the appropriate details from the release, e.g.  [https://github.com/hyperledger/besu/pull/8117/commits/1f04c5862ba38fa8d39289148ae875432f8059d0](https://github.com/hyperledger/besu/pull/8117/commits/1f04c5862ba38fa8d39289148ae875432f8059d0)
- Run with `./gradlew ethereum:referenceTests:referenceTests`
- Open `ethereum/referencetests/build/reports/tests/referenceTests/index.html`
- This ends up using `GeneralStateReferenceTestTools.executeTest` for state tests and `BlockchainReferenceTestTools.executeTest` for blockchain tests
- For debugging, you can find the appropriate pre-filled json file batched into a generated java file, e.g. `BlockchainReferenceTest_10.java` and debug in IntelliJ

### Run via kurtosis + assertor

### Run via hive

If you want to test local changes, in besu build the docker image locally with:
`./gradlew distDocker` 
and update your client file like so, using the appropriate commit hash from your locally built image (check with `docker images`).

```yaml
- client: besu
  nametag: besu-local
  build_args:
    baseimage: hyperledger/besu
    tag: 25.1-develop-701d413
```

Hive setup docs here: [Hive](https://www.notion.so/Hive-181fc61a326e80fb960ad81fe1f0f474?pvs=21) 

`./hive --sim "ethereum/eest/consume-engine" --client "besu"  --sim.buildarg fixtures=https://github.com/ethereum/execution-spec-tests/releases/download/pectra-devnet-6%40v1.0.0/fixtures_pectra-devnet-6.tar.gz --client.checktimelimit=60s --sim.parallelism=4 -sim.limit '.*tests/prague.*'` 

if you get an error that /var/run/docker.sock does not exist, 

`cd /var/run; sudo ln -s ~/.docker/run/docker.sock docker.sock`

you can specify `--client-file=client-config.yaml`

```
- client: besu
  nametag: hyperledger_besu_main
  dockerfile: git
  build_args:
    github: hyperledger/besu
    tag: main

```

## Connect to devnet 6 locally

- Download besu.json, config.yaml and genesis.ssz from [https://github.com/ethpandaops/pectra-devnets/tree/master/network-configs/devnet-6/metadata](https://github.com/ethpandaops/pectra-devnets/tree/master/network-configs/devnet-6/metadata)
- `./gradlew installDist`on latest main branches of besu and teku
- generate /tmp/jwt.hex

```
./besu/build/install/besu/bin/besu --data-path=/data/besu --rpc-http-enabled --metrics-enabled=true --metrics-host='0.0.0.0' --metrics-port=9545 --host-allowlist=* --genesis-file /data/besu/genesis.json --bootnodes="enode://fad31c0f6613e57cf7f1b6c31b0f947233b87df918f5646746f7084d3e460a5b98c16954357a6ae429edd9e176b58aaaa27316ede704a346140a78e65909e8c4@165.232.125.107:30303?discport=30303,enode://c0024c74ed4a64f9148f26405e373977ae147af797008ff054f7f68c0bb4c33ce820945439b24b2619b47ddd7a53988210a870a23b850a7da0ba03cc527f2361@64.226.84.60:30303,enode://2fb1c5fdc4335674e697fc64d9a1f5e17febe9b7433aeed9b09a72e3e86d99d76664ad457512cd98a25df11b0ebcc709f6ca1256be7e9007628475ed0d9d963a@164.90.190.204:30303?discport=30303,enode://59b19e1403dcd9dd07f608cd62565d53e5cd1c491eae1d4853e5f42877f7e5ff90e8c5ddf7762032d09aa218ec447d5c3cd5f4611c3ddfa51db8a6c7402c9884@188.166.20.100:30303?discport=30303,enode://f7da89fb160c7e1cef7c913a62eb14c9a8294765ed841d69df2787491fb887bc983c0cda502dbcc50b4249d73ce6393eb40cd8bb0f2b941d1bd11df5c60fee5c@206.189.118.198:30303?discport=30303,enode://40737ee4cef4b3eef58c741a6e84e0caf94974a276cf9f6f00cf1b1fd9c4fbcd7f800f25cdaa9bbc5b9d2e65cb6fc2fff3afc6b46321276e0db404cdf41b9940@104.248.132.138:30303?discport=30303,enode://3113ff423240964c6e9e762eae7c191ad3dcf23ff8f7905699bf94ef8916794a35cf374d19634e4eff7c01e71bf3eff3128e67aa15d92632096f84d506afa7ac@142.93.132.177:30303?discport=30303,enode://54a9e1fd7b70fc2b07919b88a2b1b2f1e2b480d704a7ecc2bb81e734ad8a2a567c7e148165333f62e0fb83c0e617b5293c26653a050d32eedb6861e9a1d0419e@144.126.231.241:30303?discport=30303,enode://169bd576e33f7ac3ce0d57c0b55732810fe863f8ef060c6d5cdd5df066e33a076680cc04a2d0877e73cd116a9d7ac50867a8af1fba023fc8dd4fca5da4a16f85@134.209.245.9:30303?discport=30303,enode://afaff7c27999dbb1e5cddde38bc45f768cb0bed1234fb0c1279a86be4cb485013f462fb028673c1c90a91e83931adbd89f2dd1287a930171804e0c64deebfb6d@167.172.182.87:30303?discport=30303,enode://fd99ca150735bd63eb6a078a7eda816ea4d1e7b3f282485f79044f932dcad0a733187ebd6c60a2a2697e128c551ab317594a9e2e78495d73f77db019b5da6db9@167.172.176.17:30303?discport=30303" --rpc-http-api=ADMIN,DEBUG,ETH,MINER,NET,TRACE,TXPOOL,WEB3 --sync-mode=FULL --data-storage-format=BONSAI --bonsai-limit-trie-logs-enabled=false --engine-jwt-secret=/etc/jwt-secret.hex
```

```
./teku/build/install/teku/bin/teku --data-path=/tmp/teku --log-destination=CONSOLE --p2p-enabled=true --rest-api-enabled --rest-api-interface=0.0.0.0 --ee-endpoint=http://localhost:8551 --ee-jwt-secret-file=/tmp/jwt.hex --metrics-enabled=true --network=./config.yaml --genesis-state=./genesis.ssz --p2p-discovery-bootnodes=enr:-LK4QE-v0HEpn0usZbxMI0vtM0LLXuROmNKYGXaJUMmE21y7EVKI19aHuAq7yg040pTzEkhhDkAawLy6iTozChOz-jEEh2F0dG5ldHOIwAAAAAAAAACEZXRoMpBQIBKjYFhVVwoAAAAAAAAAgmlkgnY0gmlwhLympd-Jc2VjcDI1NmsxoQK5IbkUmIqVgl9P2mPtdT9AkqrArvrb8L3rkKTsL3BOmoN0Y3CCIyiDdWRwgiMo,enr:-MS4QPmF9pPKEPeqC6wpP447eWy1D8DCr8ZKQgPaDSTSmuCiI4LuPZCGre9_bWJdVpo6hLLwfIb-7MBBbxbDLUK9iiABh2F0dG5ldHOIAAAAAAAAAACEZXRoMpBQIBKjYFhVVwoAAAAAAAAAgmlkgnY0gmlwhM5RFJiEcXVpY4IjKYlzZWNwMjU2azGhA__S4hBk4XcgxFkDJmIEzArw6UkGggFYjbfy2YoII0CjiHN5bmNuZXRzAIN0Y3CCIyiDdWRwgiMo --p2p-peer-upper-bound=100 --data-storage-non-canonical-blocks-enabled=true --logging=info --Xlog-include-p2p-warnings-enabled --metrics-block-timing-tracking-enabled --ignore-weak-subjectivity-period-enabled --checkpoint-sync-url=https://checkpoint-sync.pectra-devnet-5.ethpandaops.io

```