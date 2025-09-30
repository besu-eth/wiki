# Besu

|     |     |
| --- | --- |
| **Project** | For this SVG the export flag is not set! |
| **Status** | GRADUATED[](https://lf-hyperledger.atlassian.net/wiki/display/HYP/Project+Lifecycle#ProjectLifecycle-incubation) |
| **CII Badge** | [![](https://bestpractices.coreinfrastructure.org/projects/3174/badge)<br><br>](https://bestpractices.coreinfrastructure.org/projects/3174) |
| **Community** | [Discord](https://discord.com/invite/hyperledger) |
| **Working group** | [Besu Financial Services Working Group](https://lf-hyperledger.atlassian.net/wiki/display/BFFWG/) |
| **Description** | [Besu](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Hyperledger+Besu) is an Ethereum client designed to be enterprise-friendly for both public and private permissioned network use cases, with an extractable EVM implementation. It can also be run on test networks such as Holesky and Sepolia. Besu includes several consensus algorithms including Proof of Stake and Proof of Authority (IBFT 2.0, QBFT, and Clique). Its comprehensive plugin scheme is designed for modularity. |

# Key Characteristics

**What is Besu?**

Besu is an open source Ethereum client developed under the Apache 2.0 license and written in Java. It can be run on the Ethereum public network or on private permissioned networks, as well as test networks such as Holesky and Sepolia. Besu includes several consensus algorithms including PoS, PoA, and IBFT, and has a plugin scheme designed for modularity.

**What are Besu’s Features?**

Besu’s features include: 

- 
  - **The Ethereum Virtual Machine (EVM)** : The EVM is the Turing complete virtual machine that allows the deployment and execution of smart contracts via transactions within an Ethereum blockchain. It is used in conjunction with the rest of the Besu client or as a standalone library. 
  - **Consensus Algorithms:** Besu implements various consensus algorithms which are involved in transaction validation, block validation, and block production (i.e., mining in Proof of Work). They include:
    - ***Proof of Stake:*** Alongside a consensus client, Besu can be used to connect to and participate in Ethereum Mainnet proof-of-stake. 
    - ***Proof of Authority:*** Besu implements several Proof of Authority protocols. Proof of Authority consensus protocols are used when participants are known to each other and there is a level of trust between them––in a permissioned consortium network, for example.
      - *QBFT:* QBFT is the recommended enterprise-grade consensus protocol for private networks. In QBFT networks, approved accounts, known as validators, validate transactions and blocks. Validators take turns to create the next block. Before inserting the block onto the chain, a super-majority (greater than or equal to ⅔) of validators must first sign the block. 
      - *IBFT 2.0:* In IBFT 2.0 networks, transactions and blocks are validated by approved accounts, known as validators.  Validators take turns creating the next block. Existing validators propose and vote to add or remove validators. IBFT 2.0 has immediate finality. When using IBFT 2.0, there are no forks and all valid blocks are included in the main chain.
      - *Clique:* Clique is more fault-tolerant than IBFT 2.0. Clique tolerates up to half of the validators failing. IBFT 2.0 networks require greater than or equal to ⅔ of validators to be operating to create blocks. Clique does not have immediate finality. Implementations using Clique must be aware of forks and chain reorganizations occurring.
    - **(Deprecated)** ***Proof of Work*** **(Ethash):** Proof of Work is used for mining activities on Ethereum Classic.
  - **Storage:** Besu uses a RocksDB key-value database to persist chain data locally.  This data is divided into a few sub-categories:
    - **Blockchain:** Blockchain data is composed of block headers that form the “chain” of data that is used to cryptographically verify blockchain state; block bodies that contain the list of ordered transactions included in each block; and transaction receipts that contain metadata related to transaction execution including transaction logs. 
    - **World State:** Every block header references a world state via a stateRoot hash.  The world state is a mapping from addresses to accounts. Externally owned accounts contain an ether balance, while smart contract accounts additionally contain executable code and storage.
      - **Bonsai:** Bonsai storage is a novel paradigm for storing Ethereum state, built specifically for keeping Ethereum Mainnet storage requirements low. Bonsai organizes states into a new structure, to provide implicit pruning and low requirements. More details [here](https://besu.hyperledger.org/en/latest/public-networks/concepts/data-storage-formats/#bonsai-tries).
      - **Forest:** A traditional trie structure, suitable for private networks and archival nodes.
  - **P2P networking:** Besu implements Ethereum’s devp2p network protocols for inter-client communication and an additional sub-protocol for IBFT2:
    - **Discovery:** A UDP-based protocol for finding peers on the network
    - **RLPx:** A TCP-based protocol for communication between peers via various “sub-protocols”:
      - ETH Sub-protocol (Ethereum Wire Protocol): Used to synchronize blockchain state across the network and propagate new transactions.
      - IBF Sub-protocol: Used by IBFT2 consensus protocol to facilitate consensus decisions.
  - **User-facing APIs:** Besu provides mainnet Ethereum and EEA JSON-RPC APIs over HTTP and WebSocket protocols as well as a GraphQL API.  
    - **JSON-RPC**

- 
  - 
    - 
      - HTTP JSON-RPC Service
      - WebSocket JSON-RPC Service
    - **GraphQL**
  - **Monitoring:** Besu allows you to monitor node and network performance.
    - Node performance is monitored using Prometheus or the debug\_metrics JSON-RPC API method. It can be visually monitored through [Grafana](https://grafana.com/grafana/dashboards/10273-besu-overview/). 
    - Network Performance is monitored with Grafana or the [Quorum Explorer](https://github.com/ConsenSys/quorum-explorer) (part of the [Developer Quickstart](https://besu.hyperledger.org/en/stable/private-networks/tutorials/quickstart/)).
  - **(Deprecated) Privacy**: Privacy in Besu refers to the ability to keep transactions private between the involved parties. Other parties cannot access the transaction content, sending party, or list of participating parties. Besu uses a Private Transaction Manager to implement privacy. 
  - **(Deprecated) Permissioning:** A permissioned network allows only specified nodes and accounts to participate by enabling node permissioning and/or account permissioning on the network.

Besu implements the [Enterprise Ethereum Alliance](https://entethalliance.org/) (EEA) specification. The EEA specification was established to create common interfaces amongst the various open and closed source projects within Ethereum, to ensure users do not have vendor lock-in, and to create standard interfaces for teams building applications. Besu implements enterprise features in alignment with the EEA client specification. 

# Documentation

Documentation on Besu can be found here: [https://besu.hyperledger.org/](https://besu.hyperledger.org/)

# Repositories

[https://github.com/hyperledger/besu/](https://github.com/hyperledger/besu/)

[https://github.com/hyperledger/besu-docs](https://github.com/hyperledger/besu-docs)

# Get Started

Public Ethereum: [Connect to a testnet](https://besu.hyperledger.org/en/latest/public-networks/get-started/connect/testnet/)

Private networks: [Developer Quickstart](https://besu.hyperledger.org/en/stable/private-networks/tutorials/quickstart/)

# Want to contribute? 

Have Java skills and/or a knack for Ethereum development? Reach out to us in our Discord! The #besu-contributors channel is a great way to speak with devs and find some good first issues!

More info at this page - [Start Here](./besu/start-here.md)  
  
Check out [the "good first issue" label](https://github.com/hyperledger/besu/issues?q=is:open+is:issue+label:%22good+first+issue%22) on our Github!

# Communication

Mailing List

- [besu@lists.hyperledger.org](mailto:besu@lists.hyperledger.org)
  - [subscribe](https://lists.hyperledger.org/g/besu)
  - [messages](https://lists.hyperledger.org/g/besu/topics)

## Chat (for questions and ephemeral discussions)

Besu uses Discord for chat channel discussions. 

1. Go to [https://discord.com/invite/hyperledger](https://discord.com/invite/hyperledger)
2. Click Accept Invite!
3. You’re In! Find the Besu team at #besu and #besu-contributors

# Meetings

Create meeting note

  

- [Suspend APAC Contributor Call](./besu/meetings/suspend-apac-contributor-call.md)
- [Notes](./besu/meetings/notes.md)
  - [2020 Notes](./besu/meetings/notes/2020-notes.md)
    - [2020-10-27 Office Hours Notes](./besu/meetings/notes/2020-notes/2020-10-27-office-hours-notes.md)
    - [2020-09-29 Besu Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-09-29-besu-contributor-call-notes.md)
    - [2020-09-15 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-09-15-contributor-call-notes.md)
    - [2020-09-01 Besu Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-09-01-besu-contributor-call-notes.md)
    - [2020-08-18 Besu Contrubutor Call Notes](./besu/meetings/notes/2020-notes/2020-08-18-besu-contrubutor-call-notes.md)
    - [2020-08-04 Contributor Call Nodes](./besu/meetings/notes/2020-notes/2020-08-04-contributor-call-nodes.md)
    - [2020-07-21 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-07-21-contributor-call-notes.md)
    - [2020-07-07 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-07-07-contributor-call-notes.md)
    - [2020-06-23 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-06-23-contributor-call-notes.md)
    - [2020-06-09 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-06-09-contributor-call-notes.md)
    - [2020-05-26 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-05-26-contributor-call-notes.md)
    - [2020-05-12 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-05-12-contributor-call-notes.md)
    - [2020-04-28 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-04-28-contributor-call-notes.md)
    - [2020-04-14 Contributor Call](./besu/meetings/notes/2020-notes/2020-04-14-contributor-call.md)
    - [2020-03-17 Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-03-17-contributor-call-notes.md)
    - [2020-02-18 Besu Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-02-18-besu-contributor-call-notes.md)
    - [2020-02-04 Besu Contributor Call Notes](./besu/meetings/notes/2020-notes/2020-02-04-besu-contributor-call-notes.md)
    - [2020-01-21 Contributor Call](./besu/meetings/notes/2020-notes/2020-01-21-contributor-call.md)
    - [2020-01-07 Contributor Call](./besu/meetings/notes/2020-notes/2020-01-07-contributor-call.md)
  - [2022-1-31 Contributor Call notes](./besu/meetings/notes/2022-1-31-contributor-call-notes.md)
  - [2021-01-19 Office Hours Notes](./besu/meetings/notes/2021-01-19-office-hours-notes.md)
  - [2019 Notes](./besu/meetings/notes/2019-notes.md)
    - [2019-12-10 Contributor Call](./besu/meetings/notes/2019-notes/2019-12-10-contributor-call.md)
    - [2019-11-26 Contributor Call](./besu/meetings/notes/2019-notes/2019-11-26-contributor-call.md)
    - [2019-11-12 Contributor Call](./besu/meetings/notes/2019-notes/2019-11-12-contributor-call.md)
    - [2019-10-29 Contributor Call](./besu/meetings/notes/2019-notes/2019-10-29-contributor-call.md)
    - [2019-10-15 Contributor Call](./besu/meetings/notes/2019-notes/2019-10-15-contributor-call.md)
    - [2019-10-01 Contributor call](./besu/meetings/notes/2019-notes/2019-10-01-contributor-call.md)
    - [2019-09-17 Contributor call](./besu/meetings/notes/2019-notes/2019-09-17-contributor-call.md)
    - [2019-09-04 Onboarding call](./besu/meetings/notes/2019-notes/2019-09-04-onboarding-call.md)
- [Agendas](./besu/meetings/agendas.md)
  - [2025 Agendas](./besu/meetings/agendas/2025-agendas.md)
    - [2025-09-30 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-09-30-contributor-call.md)
    - [2025-09-02 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-09-02-contributor-call.md)
    - [2025-08-05 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-08-05-contributor-call.md)
    - [2025-05-13 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-05-13-contributor-call.md)
    - [2025-04-15 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-04-15-contributor-call.md)
    - [2025-03-18 Contributor Call](./besu/meetings/agendas/2025-agendas/2025-03-18-contributor-call.md)
  - [2024 Agendas](./besu/meetings/agendas/2024-agendas.md)
    - [2024-11-26 Contributor Call - US/AMEA](./besu/meetings/agendas/2024-agendas/2024-11-26-contributor-call-usamea.md)
    - [2024-09-03 Contributor Call - US/EMEA](./besu/meetings/agendas/2024-agendas/2024-09-03-contributor-call-usemea.md)
    - [2024-07-09 Contributor Call](./besu/meetings/agendas/2024-agendas/2024-07-09-contributor-call.md)
    - [2024-06-11 Contributor Call - US/EMEA](./besu/meetings/agendas/2024-agendas/2024-06-11-contributor-call-usemea.md)
    - [2024-04-16 Contributor Call - US/EMEA Friendly Time](./besu/meetings/agendas/2024-agendas/2024-04-16-contributor-call-usemea-friendly-time.md)
    - [2024-03-26 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2024-agendas/2024-03-26-contributor-call-apac-friendly-time.md)
    - [2024-03-19 Contributor Call - US/EMEA Friendly Time](./besu/meetings/agendas/2024-agendas/2024-03-19-contributor-call-usemea-friendly-time.md)
    - [2024-02-27 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2024-agendas/2024-02-27-contributor-call-apac-friendly-time.md)
    - [2024-02-20 Contributor Call - US/EMEA Friendly Time](./besu/meetings/agendas/2024-agendas/2024-02-20-contributor-call-usemea-friendly-time.md)
    - [2024-01-30 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2024-agendas/2024-01-30-contributor-call-apac-friendly-time.md)
    - [2024-01-23 Contributor Call - AMEA Friendly Time](./besu/meetings/agendas/2024-agendas/2024-01-23-contributor-call-amea-friendly-time.md)
    - [2024-01-02 Contributor Call - APAC Friendly Time - CANCELLED](./besu/meetings/agendas/2024-agendas/2024-01-02-contributor-call-apac-friendly-time-cancelled.md)
  - [2023 Agendas](./besu/meetings/agendas/2023-agendas.md)
    - [2023-12-05 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-12-05-contributor-call-apac-friendly-time.md)
    - [2023-11-28 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-11-28-contributor-call.md)
    - [2023-11-07 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-11-07-contributor-call-apac-friendly-time.md)
    - [2023-10-31 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-10-31-contributor-call.md)
    - [2023-10-10 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-10-10-contributor-call-apac-friendly-time.md)
    - [2023-10-02 Contributor Call - AMEA Friendly Time](./besu/meetings/agendas/2023-agendas/2023-10-02-contributor-call-amea-friendly-time.md)
    - [2023-09-12 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-09-12-contributor-call-apac-friendly-time.md)
    - [2023-09-05 Contributor Call - EMEA Friendly Time](./besu/meetings/agendas/2023-agendas/2023-09-05-contributor-call-emea-friendly-time.md)
    - [2023-08-15 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-08-15-contributor-call-apac-friendly-time.md)
    - [2023-08-01 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-08-01-contributor-call.md)
    - [2023-07-18 Contributor Call - APAC Friendly Time - CANCELLED](./besu/meetings/agendas/2023-agendas/2023-07-18-contributor-call-apac-friendly-time-cancelled.md)
    - [2023-07-11 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-07-11-contributor-call.md)
    - [2023-06-20 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-06-20-contributor-call-apac-friendly-time.md)
    - [2023-06-06 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-06-06-contributor-call.md)
    - [2023-05-23 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-05-23-contributor-call-apac-friendly-time.md)
    - [2023-05-09 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-05-09-contributor-call.md)
    - [2023-04-11 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-04-11-contributor-call.md)
    - [2023-04-25 Contributor Call - APAC Friendly Time - CANCELLED](./besu/meetings/agendas/2023-agendas/2023-04-25-contributor-call-apac-friendly-time-cancelled.md)
    - [2023-03-28 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-03-28-contributor-call-apac-friendly-time.md)
    - [2023-03-14 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-03-14-contributor-call.md)
    - [2023-02-28 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-02-28-contributor-call-apac-friendly-time.md)
    - [2023-02-14 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-02-14-contributor-call.md)
    - [2023-01-31 Contributor Call - AMEA Reschedule](./besu/meetings/agendas/2023-agendas/2023-01-31-contributor-call-amea-reschedule.md)
    - [2023-01-31 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-01-31-contributor-call-apac-friendly-time.md)
    - [2023-01-17 Contributor Call](./besu/meetings/agendas/2023-agendas/2023-01-17-contributor-call.md)
    - [2023-01-03 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2023-agendas/2023-01-03-contributor-call-apac-friendly-time.md)
  - [2022 Agendas](./besu/meetings/agendas/2022-agendas.md)
    - [2022-12-20 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-12-20-contributor-call.md)
    - [2022-12-06 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-12-06-contributor-call-apac-friendly-time.md)
    - [2022-11-22 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-11-22-contributor-call.md)
    - [2022-11-08 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-11-08-contributor-call-apac-friendly-time.md)
    - [2022-10-25 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-10-25-contributor-call.md)
    - [2022-10-11 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-10-11-contributor-call-apac-friendly-time.md)
    - [2022-09-27 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-09-27-contributor-call.md)
    - [2022-09-13 Contributor Call - APAC](./besu/meetings/agendas/2022-agendas/2022-09-13-contributor-call-apac.md)
    - [2022-08-30 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-08-30-contributor-call.md)
    - [2022-08-16 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-08-16-contributor-call-apac-friendly-time.md)
    - [2022-08-02 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-08-02-contributor-call.md)
    - [2022-07-19 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-07-19-contributor-call-apac-friendly-time.md)
    - [2022-07-05 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-07-05-contributor-call.md)
    - [2022-06-21 Contributor Call - APAC Friendly Time](./besu/meetings/agendas/2022-agendas/2022-06-21-contributor-call-apac-friendly-time.md)
    - [2022-05-24 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-05-24-contributor-call.md)
    - [2022-06-07 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-06-07-contributor-call.md)
      - [Make Besu questions easy to find and answer](./besu/meetings/agendas/2022-agendas/2022-06-07-contributor-call/make-besu-questions-easy-to-find-and-answer.md)
    - [2022-05-10 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-05-10-contributor-call.md)
    - [2022-04-26 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-04-26-contributor-call.md)
    - [2022-03-29 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-03-29-contributor-call.md)
    - [2022-04-12 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-04-12-contributor-call.md)
    - [2022-03-15 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-03-15-contributor-call.md)
    - [2022-03-01 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-03-01-contributor-call.md)
    - [2022-02-15 Contributor Call](./besu/meetings/agendas/2022-agendas/2022-02-15-contributor-call.md)
    - [2022-01-31 Besu Contributor Call](./besu/meetings/agendas/2022-agendas/2022-01-31-besu-contributor-call.md)
    - [2022-01-20 Besu Contributor Call](./besu/meetings/agendas/2022-agendas/2022-01-20-besu-contributor-call.md)
    - [2022-01-11 Besu Contributor Call - Off-Cycle](./besu/meetings/agendas/2022-agendas/2022-01-11-besu-contributor-call-off-cycle.md)
    - [2022-01-04 Besu Contributor Call](./besu/meetings/agendas/2022-agendas/2022-01-04-besu-contributor-call.md)
  - [2021 Agendas](./besu/meetings/agendas/2021-agendas.md)
    - [2021-12-30 Besu Contributor Call (off cycle)](./besu/meetings/agendas/2021-agendas/2021-12-30-besu-contributor-call-off-cycle.md)
    - [2021-12-07 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-12-07-besu-contributor-call.md)
    - [2021-12-21 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-12-21-besu-contributor-call.md)
    - [2021-11-09 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-11-09-besu-contributor-call.md)
    - [2021-11-23 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-11-23-besu-contributor-call.md)
    - [2021-10-11 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-10-11-besu-contributor-call.md)
    - [2021-10-26 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-10-26-besu-contributor-call.md)
    - [2021-09-28 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-09-28-besu-contributor-call.md)
    - [2021-09-13 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-09-13-besu-contributor-call.md)
    - [2021-08-31 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-08-31-besu-contributor-call.md)
    - [2021-08-16 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-08-16-besu-contributor-call.md)
    - [2021-08-03 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-08-03-besu-contributor-call.md)
    - [2021-07-19 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-07-19-besu-contributor-call.md)
    - [2021-07-06 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-07-06-besu-contributor-call.md)
    - [2021-06-21 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-06-21-besu-contributor-call.md)
    - [2021-06-08 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-06-08-besu-contributor-call.md)
    - [2021-05-24 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-05-24-besu-contributor-call.md)
    - [2021-05-11 Besu Office Hours](./besu/meetings/agendas/2021-agendas/2021-05-11-besu-office-hours.md)
    - [2021-04-26 Besu Office Hours](./besu/meetings/agendas/2021-agendas/2021-04-26-besu-office-hours.md)
    - [2021-04-13 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-04-13-besu-contributor-call.md)
    - [2021-03-30 Besu Office Hours](./besu/meetings/agendas/2021-agendas/2021-03-30-besu-office-hours.md)
    - [2021-03-16 Besu Office Hours](./besu/meetings/agendas/2021-agendas/2021-03-16-besu-office-hours.md)
    - [2021-03-02 Besu Contributor Call](./besu/meetings/agendas/2021-agendas/2021-03-02-besu-contributor-call.md)
    - [2021-02-16 Office Hours](./besu/meetings/agendas/2021-agendas/2021-02-16-office-hours.md)
    - [2021-02-02 Office Hours](./besu/meetings/agendas/2021-agendas/2021-02-02-office-hours.md)
    - [2021-01-19 Office Hours](./besu/meetings/agendas/2021-agendas/2021-01-19-office-hours.md)
  - [2020 Agendas](./besu/meetings/agendas/2020-agendas.md)
    - [2020-11-24 Office Hours](./besu/meetings/agendas/2020-agendas/2020-11-24-office-hours.md)
    - [2020-10-27 Office Hours](./besu/meetings/agendas/2020-agendas/2020-10-27-office-hours.md)
    - [2020-10-13 Hyperledger Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-10-13-hyperledger-besu-contributor-call.md)
    - [2020-09-29 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-09-29-besu-contributor-call.md)
    - [2020-09-15 Contributor Call](./besu/meetings/agendas/2020-agendas/2020-09-15-contributor-call.md)
    - [2020-09-01 Contributor Call](./besu/meetings/agendas/2020-agendas/2020-09-01-contributor-call.md)
    - [2020-08-18 Contributor Call Agenda](./besu/meetings/agendas/2020-agendas/2020-08-18-contributor-call-agenda.md)
    - [2020-08-04 Contributor Call Agenda](./besu/meetings/agendas/2020-agendas/2020-08-04-contributor-call-agenda.md)
    - [2020-07-21 Contributor Call Agenda](./besu/meetings/agendas/2020-agendas/2020-07-21-contributor-call-agenda.md)
    - [2020-07-07 Contributor Call](./besu/meetings/agendas/2020-agendas/2020-07-07-contributor-call.md)
    - [2020-06-23 Besu Contributor Call Agenda](./besu/meetings/agendas/2020-agendas/2020-06-23-besu-contributor-call-agenda.md)
    - [2020-06-09 Besu Contributor Call Agenda](./besu/meetings/agendas/2020-agendas/2020-06-09-besu-contributor-call-agenda.md)
    - [2020-05-26 Contributor Call](./besu/meetings/agendas/2020-agendas/2020-05-26-contributor-call.md)
    - [2020-05-12 Contributor Call](./besu/meetings/agendas/2020-agendas/2020-05-12-contributor-call.md)
    - [2020-04-28 Contributor call](./besu/meetings/agendas/2020-agendas/2020-04-28-contributor-call.md)
    - [2020-04-14 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-04-14-besu-contributor-call.md)
    - [2020-03-31 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-03-31-besu-contributor-call.md)
    - [2020-03-17 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-03-17-besu-contributor-call.md)
    - [2020-02-18 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-02-18-besu-contributor-call.md)
    - [2020-02-04 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-02-04-besu-contributor-call.md)
    - [2020-01-21 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-01-21-besu-contributor-call.md)
    - [2020-01-07 Besu Contributor Call](./besu/meetings/agendas/2020-agendas/2020-01-07-besu-contributor-call.md)
  - [2019 Agendas](./besu/meetings/agendas/2019-agendas.md)
    - [2019-12-10 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-12-10-besu-contributor-call.md)
    - [2019-11-26 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-11-26-besu-contributor-call.md)
    - [2019-11-12 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-11-12-besu-contributor-call.md)
    - [2019-10-29 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-10-29-besu-contributor-call.md)
    - [2019-10-15 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-10-15-besu-contributor-call.md)
    - [2019-10-01 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-10-01-besu-contributor-call.md)
    - [2019-09-17 Besu Contributor Call](./besu/meetings/agendas/2019-agendas/2019-09-17-besu-contributor-call.md)

# History

## Recent space activity

Error rendering macro 'recently-updated' : com.atlassian.confluence.search.v2.InvalidSearchException: com.atlassian.confluence.api.service.exceptions.scale.SSStatusCodeException: There was an illegal request passed to XP-Search Aggregator API : HTTP/1.1 403 Forbidden

## Space contributors

Error rendering macro 'contributors' : com.atlassian.confluence.search.v2.InvalidSearchException: com.atlassian.confluence.api.service.exceptions.scale.SSStatusCodeException: There was an illegal request passed to XP-Search Aggregator API : HTTP/1.1 403 Forbidden