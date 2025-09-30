# 2019-10-29 Contributor Call

[Recording of Call](#)

1.4 release planning

- discussed release cadence
  - AR - Danno add wiki page for this
  - Discussed breaking changes in release not in CD releases, do breaks at quarterly releases
    - Example: Disallowing comments in genesis.json
    - Example: dropping support for Java 8
- 1.4 aimed release for end of Feb, 26/27
  - RC 12/13 Feb
- Call from community about desired features
  - PegaSys contributions
    - End to End TLS between external programs
      - JSON-RPC for EthSigner
      - ? for Orion
    - More Tracing APIs
      - More like Parity's style, currently have Geth's style.
    - TPS/QPS performance improvements
      - TPS focus for private networks
      - QPS focus for public networks (like mainnet
    - Support Berlin HF if Berlin HF happens (maybe)
      - This is driven by AllCoreDevs
    - Node multi-tenancy (conceptual, design TBD)
      - One node isolating data for multiple consortial clients
  - ETC Support
    - Targeting mid-November, shipping in 1.3 CD releases
  - Privacy Group Management
    - Needs to be able to add precompiles via plugins
  - Any contributions as they roll in
- ETC update
  - All ETC hard forks implemented 
  - Syncing up to block 4 million
  - Had a bottleneck at 1.5mil
    - Likely because of shared network ID
    - May be able to write an ETC peer validator
  - Bob Noted PRs for
    - Switching to fast sync by default
      - Discussing on for public networks, off for private networks by default.
      - Interacts with pruning feature
    - Stratum mining from Antoine from Whiteblock
- CI/CD
  - Josh isn't here,
  - Brian discussed moving to CircleCI vs Azure Pipelines vs GitLabCI
    - Brian wants convergence to one CI provider, but there is no formal policy prohibiting it.
- Grid Demo (not HL Grid, the EF project)
  - Deferred to a future meeting

  

Open discussion

- PegaSys posts bounties, keep an eye on Gitcoin
- EthWaterloo/EthDenver/EthCC
  - Waterloo - Nov 8-10
  - Denver - Feb 15-17
  - EthCC (Ethereum Community Conference Paris France) - March 3-5 - Bob Summerwill talking
- Status on Trie Optimization
  - Not in the roadmap currently.
  - Danno is investigating alternate storage engines, HaloDB, etc.
- Discussion about optimizations and JVMs
- Hyperledger Caliper
  - Supports Besu in 0.2
  - First Cross HLP contributions