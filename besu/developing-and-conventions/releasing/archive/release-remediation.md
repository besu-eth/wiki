# Release Remediation

# What to do when a defect has been discovered in a release version of Besu?

## GitHub

Nothing. 

The history is GitHub (release tags and commits) are never rewritten when a defect or bug is discovered. It serves as a record of history, documented what has happened over the course of Besu's lifetime.

## Binary Artefact

When a defect is found that causes data corruption in common cases or significant security breach, then that artefact may be removed from the Binary Artefact store.

## Changelog and Communication 

For significant defects including where a release is not usable in common cases, the [Changelog](https://github.com/hyperledger/besu/blob/master/CHANGELOG.md) is updated and a post is made to the besu and besu-contributors channels on RocketChat.