# Building from source

## Prerequisites

- Java 25 (required to build Besu)
  - This was introduced in [besu-eth/besu#10539](https://github.com/besu-eth/besu/pull/10539).
- Git
- For macOS: macOS High Sierra 10.13 or later
- For Windows: Besu is currently supported only on 64-bit versions of Windows, and requires a 64-bit version of JDK/JRE.

## Checkout source code

```bash
git clone --recursive https://github.com/besu-eth/besu.git
cd besu
```

## Create a fork (for contributors)

If you plan to submit PRs, fork `besu-eth/besu` in GitHub and set your remotes:

```bash
git remote -v
git remote rename origin upstream
git remote add origin https://github.com/<your-github-user>/besu.git
```

After this, `upstream` points to the main Besu repo and `origin` points to your fork.

## See available Gradle tasks

```bash
./gradlew tasks
```

## Build from source

Build the distribution binaries:

```bash
./gradlew installDist
```

## Run from locally built binaries

Show help:

```bash
cd build/install/besu
./bin/besu --help
```

Run Besu with default options:

```bash
cd build/install/besu
./bin/besu
```

Run Besu with custom options:

```bash
cd build/install/besu
./bin/besu --discovery-enabled=false --data-path=/tmp/besutmp
```

## Building and running on Windows

To run `gradlew` on Windows, set `JAVA_HOME` to your Java 25 installation directory. Example:

```text
JAVA_HOME=C:\Program Files\Java\jdk-25
```

If you use WSL and run Besu with DNS discovery, see:

- [besu-eth/besu#3046](https://github.com/besu-eth/besu/issues/3046)

## Running tests

Use the common Gradle targets:

```bash
./gradlew build
./gradlew integrationTest
./gradlew acceptanceTest
./gradlew ethereum:referenceTests:referenceTests
```

For more test guidance, see [Developing and Conventions - Testing](Developing-and-Conventions-Testing).
