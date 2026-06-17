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

## **Hive tests** 

A suite of end to end client tests that are not invoked directly is provided here, [https://github.com/ethereum/hive](https://github.com/ethereum/hive). These tests are run against all clients and results can be seen at [https://hive.ethpandaops.io/](https://hive.ethpandaops.io/).

### Running Hive Tests

- **consensus**

  ```bash
  sudo ./hive --sim consensus --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
  ```

- **graphql**

  ```bash
  sudo ./hive --sim graphql --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
  ```

- **devp2p**

  ```bash
  sudo ./hive --sim devp2p --loglevel 6 --docker-noshell --client besu_latest --sim.parallelism 1 --sim.rootcontext
  ```

- **sync**

  ```bash
  sudo ./hive --sim ethereum/sync --loglevel 6 --docker-noshell --client besu_latest,openethereum_latest,go-ethereum_latest --sim.parallelism 1 --sim.rootcontext
  ```
