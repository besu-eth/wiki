# Testing

## **Run tests** 

All the unit tests are run as part of the build, but can be explicitly triggered with:

```
./gradlew test

```

The integration tests can be triggered with:

```
./gradlew integrationTest

```

The reference tests (described below) can be triggered with:

```
./gradlew referenceTest

```

The acceptance tests can be triggered with:

```
./gradlew acceptanceTest
```
```
  

```

## **Ethereum reference tests** 

On top of the project proper unit tests, specific unit tests are provided to run the Ethereum reference tests available at [https://github.com/ethereum/tests](https://github.com/ethereum/tests) and described at [http://ethereum-tests.readthedocs.io/en/latest/](http://ethereum-tests.readthedocs.io/en/latest/). Those are run as part of the unit test suite as described above, but for debugging it is often convenient to run only a subset of those tests. For example, run only Frontier general state tests with: 

```
./gradlew :ethereum:org.hyperledger.besu.ethereum.vm:referenceTest -Dtest.single=GeneralStateTest -Dtest.ethereum.state.eip=Frontier

```

Or only the tests that match a particular pattern with something like:

```
gradle :ethereum:org.hyperledger.besu.ethereum.vm:test -Dtest.single=GeneralStateTest -Dtest.ethereum.include='^CALLCODE.*-Frontier'

```

For more details, see the comment on the `test` target in the top level `build.gradle` file.

```
  

```

## **Hive tests** 

A suite of end to end client tests that are not invoked directly is provided here, [https://github.com/ethereum/hive](https://github.com/ethereum/hive). These tests are run against all clients and results can be seen at [https://hivetests.ethdevops.io/](https://hivetests.ethdevops.io/).

### Running Hive Tests

- consensus
  - ```
sudo ./hive --sim consensus --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
```
- graphql
  - ```
sudo ./hive --sim graphql --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
```
- devp2p
  - ```
sudo ./hive --sim devp2p --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
```
- sync
  - ```
sudo ./hive --sim ethereum/sync --loglevel 6 --docker-noshell --client besu_latest,openethereum_latest,go-ethereum_latest --sim.parallelism 1 --sim.rootcontext
```

### Known Failures

Currently there is 1 consensus test and 4 sync tests that are failing. The consensus test is believed to be performance related and the sync tests involve clients which are not properly configured within the test suite.

- failing consensus tests
  - CALLBlake2f\_MaxRounds\_d0g0v0\_Istanbul

- failing sync tests  
  - sync besu -> openethereum
  - sync besu -> trinity
  - sync besu -> aleth
  - sync nethermind -> besu

  

## **Enterprise oriented testing**

Currently the acceptance tests cover both public chain and enterprise/permissioned chains to some degree. For example "BftMiningAcceptanceTest" tests both IBFT and QBFT with basic single-node and 4-node chains, mainly submitting a small number of transactions to transfer value between accounts. The soak-testing that takes place on every Besu release does not exercise BFT chains any more than that acceptance tests that run on each PR, since the soak testing focuses on syncing with public chains.

It would be useful to have an easy way for Besu to perform more exhaustive testing of enterprise/permissioned chains on every release, and on an ad-hoc basis.

As a starting point, the following is a list of test scenarios that would be useful in validating longer running BFT chains:

- High throughput transaction tests using the **sequenced** transaction pool, running at high TPS for a minimum of a few hours
  - "High throughput" in this context would typically mean 400+ TPS with 2-second block periods 
  - Single validator to prove basic performance hasn't been regressed
  - Multi validator to prove any changes in the consensus code haven't degraded overall performance
- Chain & state integrity tests when upgrading between versions of Besu
  - Validating that the DB/storage layer retains state correctly during an upgrade
- Chain downgrade testing
  - Either validating that an accidental downgrade is prevented from occurring, or that a downgrade works correctly without loss of state
- Long running medium-TPS (e.g. 200TPS) soak test, configurable to run 1→N hours with periodic transaction submissions & state checks incorporated into the test
  - Should be easy to run without complicated setup (e.g. a new gradle task that isn't included in the current build tasks but can be manually run)
- Transition between milestones over a period of time, e.g.
  - Start with berlin
  - Run N hours
  - Transition to london
  - Run N hours
  - Transition to shanghai
  - Run N hours