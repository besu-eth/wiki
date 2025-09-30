# Proposal - Besu maintainers become docs maintainers

**Background**

Currently the [process](https://github.com/hyperledger/besu-docs/blob/master/MAINTAINERS.md) for becoming a besu-docs maintainer mirrors the [process](https://github.com/hyperledger/besu/blob/master/MAINTAINERS.md) for becoming a besu maintainer, but based on besu-docs contributions rather than besu code contributions.

However this leads to the issue

- besu developers contribute to the docs but none have so far met the requirement for "5 significant contributions" in order to become a besu-docs maintainer
- small number of besu-docs maintainers is a bottleneck for getting PRs approved.

The besu-docs repo has CI steps to check formatting, grammar, validity of internal and external HTTP links. 

All changes to besu-docs also require separate approval. 

**Proposal** 

Essentially relax the first requirement of the process for ie "The proposed maintainer authors and has accepted five significant changes".

Since we trust besu maintainers to make changes to the code, this proposal is to also trust those individuals to make changes to the related docs. Individuals need to be aware of their areas of expertise. Just as we expect besu maintainers to use their judgment when reviewing besu PRs, we expect besu-docs maintainers to use their judgment when reviewing besu-docs PRs. If the change is significant, defer to someone with expertise in that area.

Proposal:

- ask for volunteers from current Besu maintainers become besu-docs maintainers
- current besu-docs maintainers raise PR to add none/some/all of those volunteers (considering their contributions to besu-docs so far), and this PR requires approval as per the [process](https://github.com/hyperledger/besu-docs/blob/master/MAINTAINERS.md) 
- the rest of the process is followed as-is
- existing besu-docs maintainers remain besu-docs maintainers
- still keep the separate [process](https://github.com/hyperledger/besu-docs/blob/master/MAINTAINERS.md) for someone to become a besu-docs maintainer without first becoming a besu maintainer.