# Besu 2022 Vision

Hyperledger Besu is Hyperledger's Principal Ethereum project. It is focused around 3 key pillars: a fully functional client for public networks, a customizable client for private networks, and libraries to support the use of Ethereum technologies in Besu and other projects.

- Fully Functional Client for Public Networks  
Besu explicitly and "out of the box" supports the following networks, including planned future upgrades  
  - Ethereum Mainnet
    - Pre-Merge Ethash Proof-of-Work Client
    - Post-Merge Execution Client, pairablre with any fully-functional Consensus Client such as Lighthouse, Loadstar, Nimbus, Prysm, or Teku
  - Ethereum Mainnet Testnets
  - Ethereum Classic
  - Ethereum Classic Testnets
- Customizable Client for Private Networks
  - Multiple Consensus Engines such as Clique, IBFT2, or QBFT.
  - Optional private transaction technology
  - Optional Integration with Privae Enclaves such as Tessera
  - Optional  Node Access
- Libraries to support the use of Ethereum technologies
  - EVM Engine Library

  

To support these 3 pillars are the following 6 systems.

- EVM Engine
- Consensus Protocols
- Peer-to-peer communications
- JSON-RPC Communications
- Data Storage
- Block Production