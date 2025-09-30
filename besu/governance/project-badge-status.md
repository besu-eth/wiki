# Project Badge Status

# Legal

A license check is performed as a part of each build. (Here's [one from 22 Jun 2021](https://app.circleci.com/pipelines/github/hyperledger/besu/9382/workflows/c7effe7e-5ea3-4c69-85fb-1b9cb6573c5e/jobs/49241/steps?invite=true#step-109-20)).  If any dependency reports a license from anything other than the [permitted list](https://github.com/hyperledger/besu/blob/master/gradle/check-licenses.gradle#L32) a build error occurs and the distribution is not generated.

# Decentralized

[LFX Analytics Report](https://tinyurl.com/yht3mfkz)

Just under a quarter of all contributions come from outside ConsenSys Quorum (Protocols, formerly known as PegaSys, was merged with ConsenSys Quorum)

The top committing maintainer from each company over the last year:

- ConsenSys - Sally MacFarlane
- Splunk - Antoine Tolume
- Chainsafe - Edward Mack
- <No Affiliation> - Danno Ferrin

Hyperledger Besu is critical infrastructure for both ConsenSys and the Ethereum Classic Cooperative, who both are committed to maintain the project for the Ethereum Mainnet and Ethereum Classic chains respectively. Both companies would independently maintain the project if required. 

# Release

Hyperledger Besu maintains a roughly bi-weekly release schedule with roughly quarterly to three-times a year major releases cycles.

All releases can be seen in the [Besu Github Repo](https://github.com/hyperledger/besu/releases), and [future anticipated release dates in the Wiki](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Future+Release+Dates).

Besu's [roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap) is mostly driven by two external concerns: the Enterprise Ethereum Alliance specification and Ethereum Mainnet hard-forks (and to a lesser extent Ethereum Classic, which *mostly* aligns with Ethereum Mainnet)

# Testing

Besu has robust [unit](https://app.circleci.com/pipelines/github/hyperledger/besu/9386/workflows/0cb3febf-3459-45e5-949c-a8f01586db7e/jobs/49271), [integration](https://app.circleci.com/pipelines/github/hyperledger/besu/9386/workflows/0cb3febf-3459-45e5-949c-a8f01586db7e/jobs/49276), and [acceptance](https://app.circleci.com/pipelines/github/hyperledger/besu/9386/workflows/0cb3febf-3459-45e5-949c-a8f01586db7e/jobs/49272) [tests](https://app.circleci.com/pipelines/github/hyperledger/besu/9386/workflows/0cb3febf-3459-45e5-949c-a8f01586db7e/jobs/49275) run with each main branch build that validate Besu behaves as expected, as well as [reference tests](https://app.circleci.com/pipelines/github/hyperledger/besu/9386/workflows/0cb3febf-3459-45e5-949c-a8f01586db7e/jobs/49270) maintained by Ethereum core developers to check for mainnet standards compliance. These are run as part of every commit and often do catch unintended behavior changes.

# Documentation

Besu maintains a [ReadTheDocs site](https://besu.hyperledger.org/en/stable/).  Documentation includes [RPC interfaces](https://besu.hyperledger.org/en/stable/Reference/API-Methods/), [server deployment](https://besu.hyperledger.org/en/stable/HowTo/Deploy/Cloud/), [dApp development](https://besu.hyperledger.org/en/stable/HowTo/Develop-Dapps/Truffle/), and more general documentation such as [architectural structure](https://besu.hyperledger.org/en/stable/Concepts/ArchitectureOverview/).

# Alignment

The [Besu main wiki page](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Hyperledger+Besu) lists the main use cases and specific features.

As a standard Etheruem client, Hyperledger Besu interacts with all other Hyperledger projects that interface with Ethereum, specifically Avalon, Cactus, and Caliper.  Besu also works with a number of Labs projects, such as Firefly, Blockchain Automation Framework, and Yui.

# Infrastructure

Hyperledger Besu is fully hosted on Hyperledger Infrastructure: [GitHub](https://github.com/hyperledger/besu) for source control, [Discord](https://discord.gg/hyperledger) for Chat, [Hyperledger email list](https://lists.hyperledger.org/g/besu/topics) (although Discord is the dominant communication channel), builds and release are run on [CircleCI](https://app.circleci.com/pipelines/github/hyperledger/besu), and [repolinter](https://github.com/hyperledger/besu/actions/runs/961385130) verifying conformance to the common repository structure.

# CII

The most recent [CII report for Hyperledger Besu](https://bestpractices.coreinfrastructure.org/en/projects/3174).