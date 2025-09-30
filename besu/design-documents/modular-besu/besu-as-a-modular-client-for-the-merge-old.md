# Besu as a Modular Client for the Merge (OLD)

  

- [Considerations common to both approaches](#considerations-common-to-both-approaches)
- [Approach #1 “Hyperledger/Besu as Debian”](#approach-1-hyperledgerbesu-as-debian)
- [Approach #2 “An Execution Engine Shell Project”](#approach-2-an-execution-engine-shell-project)

  
  

Considerations for this work: 

*The merge is ‘different’.  The switch from proof-of-work to proof-of-stake changes the behavior of the client significantly.  There are additional endpoints served from a new \`engine\` network service which will be differently secured than existing json-rpc or web sockets services.  Knowing when to make the switch from one to the other also does not follow the ‘hard fork’ strategy from previous ethereum upgrades.  Also, presumably only ethereum mainnet (and its test nets) would ever make this transition.*

*Other layer1 evm chains are unlikely to need an execution engine client.  However, layer2’s might.  This* [*thread from protolambda*](https://docs.google.com/document/d/1LqtQcjxx5smMF43qvkbwp3Q1dNkTev1KB0BzvbE7dSI/edit) *highlights the potential for an execution engine to be leveraged in rollups.  Having a clean execution engine module would likely be useful and less cluttered than trying to adapt besu to an L2 use case.*  

*Lastly, we are working on incorporating MEV strategies into besu.  MEV so far seems to be only a consideration for ethereum mainnet and the notion of splitting the block producer role into two roles* [*blockBuilder/blockProposer*](https://ethresear.ch/t/proposer-block-builder-separation-friendly-fee-market-designs/9725) *likely would not make sense outside of the context of ethereum mainnet and MEV auctions.*  

## **Considerations common to both approaches**

- Pros
- The effort to modularize is underway already for the evm
- This dovetails nicely with the need to have pluggable MEV strategies 
- Risks
- Finding the right ‘bounded context’ for libraries is non-trivial
- The effort of refactoring Besu into modules becomes critical-path for having a besu-based execution client
- Changes the value proposition of the project - no longer is besu “an ethereum mainnet ready client”.  This is going to be the case post-merge anyway, but it is worth pro-actively redefining the message.
- Adds devops considerations for publishing modules 
- Mitigation
- We can initially rely on the existing submodules for library bounds
- We can continue to pursue a branch based approach for an execution client in parallel until we have clarity and modularization 

## **Approach #1 “Hyperledger/Besu as Debian”**

1. Split up the current monolithic besu artifact into a group of reusable libraries which are published individually
2. Rather than a monolithic artifact generate distribution-specific artifacts within the project.  An example of a distribution artifact might be “ethereum execution engine”, “ETC mainnet ready client”, “Optimistic Besu”, etc.  
3. External projects that wish to leverage besu artifacts and/or build a 3rd party Besu distribution are able to leverage the published besu artifacts

  

This would keep hyperledger/besu as a central project that natively supports a variety of use-cases via use-specific distribution artifacts.  This would be different from the current only in that there would not be a single monolithic binary.

- Pros
- Teku can directly integrate/implement besu for its default execution engine
- Enables different “distributions” of Besu, with artifacts custom tailored for individual chains, rollups, and/or applications
- Risks
- Might present some political challenges, we would have to solicit buy-in from Hyperledger TSC and contributors for example
- Would have to do distribution-specific acceptance tests for each artifact.  This would require additional devops and CI plumbing
- Timeline
- ? (incremental approach)

## **Approach #2 “An Execution Engine Shell Project”**

Create a new project for the execution engine, leveraging the hyperledger/besu modules.  Rewrite, override or extend the portions of besu necessary to deliver a lean execution client without introducing any of the ethereum PoS merge code into besu.  This would be a step in the direction of treating hyperledger/besu as more of a general purpose reference implementation of its libraries, rather than an “ethereum mainnet ready client”.

- Pros
  - Less need to coordinate with other concerns: enterprise, other public mainnets
  - Submodules and functionality that is unrelated to ethereum mainnet are just unimported
  - Onboarding of new PE may be faster - no need to understand the whole codebase, just the specific rules of the execution client.
  - Lower cyclomatic complexity would inevitably lead to better performance
  - A standalone execution engine could be leveraged in rollup implementations
- Greater simplicity
- Performance
- Integration to new services
- Cons
- Inevitable drift from re-implemented portions of besu, causing duplication of work for bugfixes and shared features
- Likely no resources or support from besu-contributors and/or hyperledger org
- Work on the execution engine would be split across multiple repositories Hyperledger/Besu and Consensys/besu-engine (for example)

  

- Timeline
- 6-9 months; relies on the modularization of besu to begin in earnest 

  

**Technical proposal**

[https://lf-hyperledger.atlassian.net/wiki/display/BESU/Design+Documents](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Design+Documents)