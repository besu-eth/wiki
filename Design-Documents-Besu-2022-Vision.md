# Besu 2022 Vision

> [!NOTE]
> This is a historical design document from 2022. It is preserved as a record of the project vision at that time. Besu is now part of Linux Foundation Decentralized Trust.

Besu is focused around 3 key pillars: a fully functional client for public networks, a customizable client for private networks, and libraries to support the use of Ethereum technologies in Besu and other projects.

- Fully functional client for public networks. Besu explicitly and "out of the box" supports the following networks, including planned future upgrades:
  - Ethereum Mainnet
    - Pre-Merge Ethash Proof-of-Work client
    - Post-Merge execution client, pairable with any fully-functional consensus client such as Lighthouse, Lodestar, Nimbus, Prysm, or Teku
  - Ethereum Mainnet testnets
  - Ethereum Classic
  - Ethereum Classic testnets
- Customizable client for private networks
  - Multiple consensus engines such as IBFT2 or QBFT
  - Optional private transaction technology
  - Optional integration with private enclaves such as Tessera
  - Optional node access
- Libraries to support the use of Ethereum technologies
  - EVM engine library

To support these 3 pillars are the following 6 systems:

- EVM engine
- Consensus protocols
- Peer-to-peer communications
- JSON-RPC communications
- Data storage
- Block production
