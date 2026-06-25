# Project Badge Status

[![OpenSSF Best Practices](https://www.bestpractices.dev/projects/3174/badge)](https://www.bestpractices.dev/projects/3174)

## Legal

A dependency license check runs as part of every build. In CI, the `checkLicense` Gradle
task runs on each pull request, and the rest of the pipeline depends on it passing.
If any dependency reports a license that isn't on the permitted list in
[`gradle/allowed-licenses.json`](https://github.com/besu-eth/besu/blob/main/gradle/allowed-licenses.json), the
`checkLicense` task fails and the build does not pass.
A dependency license report is also bundled into the distribution as **license-dependency.html**.

## Contributors

Besu is open source (Apache 2.0) and developed in the open at
[github.com/besu-eth/besu](https://github.com/besu-eth/besu), with contributions
from maintainers, independent developers, and several organizations.

The majority of contributions currently come from Consensys, with additional
contributions from the wider community. For an up-to-date breakdown of
contributors, organizations, and activity, see the
[LFX Insights dashboard for Besu](https://insights.linuxfoundation.org/project/besu/contributors).

## Release

Besu follows a CalVer versioning scheme (`YY.M.minor`) and ships a new release
roughly once a month. Additional releases are made as needed to align with
Ethereum network upgrades.
All releases are published in the
[Besu GitHub repository](https://github.com/besu-eth/besu/releases).

Besu's roadmap is driven primarily by Ethereum Mainnet hard forks. Out of the box
it can also sync several other networks selectable via `--network`, including
Ethereum test networks and other EVM networks such as Linea.

## Testing

Besu has a robust automated test suite, including unit, integration, and acceptance tests
that validate Besu behaves as expected, plus reference tests maintained by
Ethereum core developers to check Mainnet standards compliance. These run in CI
(GitHub Actions) on every pull request and in the merge queue before changes are
merged to `main`.

See the workflow runs in the
[Besu GitHub Actions tab](https://github.com/besu-eth/besu/actions).

## Documentation

Besu maintains a [documentation site](https://docs.besu-eth.org/) created using Docusaurus. The documentation source repository is [besu-eth/besu-docs](https://github.com/besu-eth/besu-docs).

## Alignment

The [Besu main wiki page](Home) lists the main use cases and specific features.

As a standard Ethereum client, Besu interacts with all other Linux Foundation
Decentralized Trust (LF Decentralized Trust) projects that interface with
Ethereum, specifically Avalon, Cactus, and Caliper. Besu also works with a
number of Labs projects, such as Firefly, Blockchain Automation Framework, and
Yui.

## Infrastructure

Besu is a LF Decentralized Trust project, developed in the open on GitHub at
[github.com/besu-eth/besu](https://github.com/besu-eth/besu) for source control.
Community discussion happens primarily on the Hyperledger
[Discord](https://discord.com/invite/hyperledger). Builds, tests, and releases run
on **GitHub Actions** (see the
[workflows](https://github.com/besu-eth/besu/tree/main/.github/workflows) and the
[Actions tab](https://github.com/besu-eth/besu/actions)), which also runs
[repolinter](https://github.com/todogroup/repolinter) to verify the repository
conforms to the common repository structure.

## CII

The most recent [CII report for Besu](https://bestpractices.coreinfrastructure.org/en/projects/3174).