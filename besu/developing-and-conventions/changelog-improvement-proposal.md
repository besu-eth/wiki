# Changelog Improvement Proposal

Besu changelog management

The file is ever-growing [https://github.com/hyperledger/besu/blob/main/CHANGELOG.md](https://github.com/hyperledger/besu/blob/main/CHANGELOG.md)

Contains outdated links and content (eg documentation updates from when besu docs were part of besu repo). This results in PRs such as [https://github.com/hyperledger/besu/pull/7558](https://github.com/hyperledger/besu/pull/7558) which are updating old links

Propose to remove old content from the changelog

- first, remove previous releases from the changelog and keep Unreleased section only
- add changes to the changelog with PRs as we do now under Unreleased
- when we do a release, the contents of the changelog become the release notes for that release, and the changelog gets wiped - Unreleased section is empty again

One reason for not doing this is that it makes github the only option for users to see the release notes, however now we use github to serve the releases themselves so that reason seems less compelling.

One advantage of having the changelog in a single file is that it's easy to search.

An alternative proposal which would remediate the broken link issue - remove docs updates from the changelog - [https://github.com/hyperledger/besu/pull/7562](https://github.com/hyperledger/besu/pull/7562)