# Building and Testing

## **Prerequisites** 

- Java 11+ 
- For Mac installations: MacOS High Sierra 10.13 or later

**Note**: Besu is currently supported only on 64-bit versions of Windows, and requires a 64-bit version of JDK/JRE. We recommend that you also remove any 32-bit JDK/JRE installations.

## **Quickstart**

```
git clone --recursive [https://github.com/hyperledger/besu](https://github.com/hyperledger/besu)  
cd besu  
./gradlew build   
./gradlew integrationTest
```

## **Checkout source code**

```
git clone --recursive git@github.com:hyperledger/besu.git

```

or

```
git clone --recursive https://github.com/hyperledger/besu
```

## **See what tasks are available** 

To see all of the gradle tasks that are available:

```
cd besu
./gradlew tasks  
```

## **Build from source**

**Note**: On Windows, to run `gradlew`, you must have the **JAVA\_HOME** system variable set to the Java installation directory. For example: `JAVA_HOME = C:\Program Files\Java\jdk1.8.0_181`

Build the distribution binaries: 

`cd besu`

`./gradlew installDist`

  

Run Besu:

`cd build\install\besu`  
`./bin/besu --help`

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

The system tests can be triggered with:

```
./gradlew smokeTest

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