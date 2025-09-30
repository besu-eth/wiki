# Using Hive Test Suite

## Online results

This dashboard shows the current status

- [https://hive.ethpandaops.io/](https://hive.ethpandaops.io/)

There are suite specific issues opened and [tagged](https://app.zenhub.com/workspaces/besu-team-65de4730380c1800c30a9f3a/board?labels=hive&repos=206414745) with `hive` for us to mutex on. Feel free to break those into smaller pieces of work if warranted.

## Build

- gh repo clone ethereum/hive
- cd hive
- go build .

## Config

Update the file *clients\_pectra.yaml* with the branch and GitHub to be used, if you’re testing against a branch that exists in the main repo

`client: besu`  
  `nametag: 4844-git # the name tag for the docker image.`  
  `dockerfile: git`  
  `build_args:`  
    `github: hyperledger/besu # the fork to use in the test. For example: “my-fork/besu”`  
      `tag: 4844-devnet-5b # the branch to be used in the test`

OR if you’re doing local development, a convenient way to test changes is to run

`gw distDocker`

`docker image ls hyperledger/besu | head`

then copy the docker tag into a config file eg

```
- client: besu
  nametag: besu-local
  build_args:
    baseimage: hyperledger/besu
    tag: 25.3-develop-2df5428

```

At least in consume-engine and consume-rlp, the hive test results also include commands to run those individual tests. It’s not *quite* right currently (EF team are aware) but it’s close.

example: the test output says

> Command to reproduce entirely in hive:

```
./hive --sim ethereum/eest/consume-rlp --client-file <('{"client":"besu","nametag":"default","dockerfile":"git","build_args":{"github":"hyperledger/besu","tag":"main"}}') --client besu_default --sim.limit "tests/cancun/eip4844_blobs/test_blob_txs.py::test_insufficient_balance_blob_tx[fork_Cancun-blockchain_test_from_state_test--exact_balance_minus_1-tx_max_fee_per_blob_gas_multiplier_10000-no_calldata-tx_value_1-tx_max_priority_fee_per_gas_7-tx_max_fee_per_gas_7-access_list]"

```

what actually works:

```
./hive --sim ethereum/eest/consume-rlp --client-file=clients_pectra.yaml  --client besu --sim.limit "id:tests/cancun/eip4844_blobs/test_blob_txs.py::test_insufficient_balance_blob_tx[fork_Cancun-blockchain_test_from_state_test--exact_balance_minus_1-tx_max_fee_per_blob_gas_multiplier_10000-no_calldata-tx_value_1-tx_max_priority_fee_per_gas_7-tx_max_fee_per_gas_7-access_list]” 

```

# sim what

There are lots of different hive suites to run. The suite is chosen with the `--sim` arg.

Note if you’re running locally, some suites take a long time, so you usually want to run a subset, using the `--sim.limit` arg. Note `.*` is used for wildcard match in the regex.

example - run prague consume-engine tests ~ 30 min

`./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file="clients_pectra.yaml" --sim.buildarg "fixtures=https://github.com/ethereum/execution-spec-tests/releases/download/v4.2.0/fixtures_develop.tar.gz" --client.checktimelimit=60s --sim.parallelism=4 -sim.limit ".*tests/prague.*"`

You can also use the `collectonly` prefix if you want to know which or how many tests will match - like dry-run.

`./hive --sim "ethereum/eest/consume-engine" --client "besu" --client-file="clients_pectra.yaml" --sim.buildarg "fixtures=https://github.com/ethereum/execution-spec-tests/releases/download/v4.2.0/fixtures_develop.tar.gz" --client.checktimelimit=60s --sim.parallelism=4 -sim.limit "collectonly:.*tests/prague.*"`

## View Results

- cd cmd/hiveview 
- go build
- ./hiveview --serve --logdir ../../workspace/logs
- From the Hive folder:  
./cmd/hiveview/hiveview --serve --logdir ./workspace/logs
- Go to [http://127.0.0.1:8080/](http://127.0.0.1:8080/)

## Local differences

Be aware, there are some that fail locally but pass in automated hive. So before you spend ages debugging a test, check to see if it's actually passing in the pandaops version

example - this one fails locally but passes in hive - CI `Invalid Missing Ancestor Syncing ReOrg, StateRoot, EmptyTxs=False, CanonicalReOrg=False, Invalid P9 (Cancun)` 

## Useful

**Caution**: when using the nocache option I have had issues with being unable to build the docker image (SHA hash mismatch with downloading ubuntu install packages).

To Rebuild the image when the branch is updated add -docker.nocache besu

\-docker.output will log useful information in case of failure during the build process.

## To debug a test

I believe the easiest way to debug is to run a node with the genesis file used in the test and manually call the engine/rpc methods using postman:

To get the genesis file, click the log in the logs column.

The genesis file will be the first thing that is logged.

Search for starting main client. It will show you the parameters that Hive used to run Besu:

Finally, you can find the calls that Hive is doing by expanding the test name:

Then you can get the calls and use postman to replicate the test.

You can run a node with the same configuration and attach the IDE to the process and debug normally.