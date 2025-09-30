# Mainnet activity log H2 2022

# *In-Progress Reports*

- *Add your contributions under your maintainer organization. If your org is not listed, please add it.*
- *GitHub query that may help \`is:pr author:xyz label:mainnet closed:>2022-07-01\`*

## Maintainer org: Hedera

Contact name -

Contact email -

### Maintainer github handle: shemnon

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs: 

Details on mainnet contributions

...

## Maintainer org: Ethereum Classic Cooperative

Contact name -

Contact email -

### Maintainer github handle: diega

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs: 

Details on mainnet contributions

...

## Maintainer org: ConsenSys

Contact name - Grace Hartley

Contact email - grace.hartley@consensys.net

### Maintainer github handle: gezero

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs:

Details on mainnet contributions

### Maintainer github handle: macfarla

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs: [https://github.com/hyperledger/besu/pulls?q=is:pr+author:macfarla+label:mainnet+closed:>2022-07-01+](https://github.com/hyperledger/besu/pulls?q=is%3Apr+author%3Amacfarla+label%3Amainnet+closed%3A%3E2022-07-01+)

Details on mainnet contributions:

Peering improvements

- [Peering logging](https://github.com/hyperledger/besu/pull/4142)
- [lower bound peer limit](https://github.com/hyperledger/besu/pull/4200)
- [Remove connections if they are already disconnected](https://github.com/hyperledger/besu/pull/4304)
- [P2P: Connect to maintained connections at startup](https://github.com/hyperledger/besu/pull/4543)
- [Remove duplicate registration of peers connect/disconnect](https://github.com/hyperledger/besu/pull/4073)
- [Logging: peer table refresh](https://github.com/hyperledger/besu/pull/4391)

Block processing

- [Ensure invalid new payload is logged at DEBUG level](https://github.com/hyperledger/besu/pull/4520)

### Maintainer github handle: mark-terry

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs: [https://github.com/hyperledger/besu/pulls?q=is:pr+author:mark-terry+label:mainnet+closed:>2022-07-01](https://github.com/hyperledger/besu/pulls?q=is%3Apr+author%3Amark-terry+label%3Amainnet+closed%3A%3E2022-07-01)

Details on mainnet contributions:

RPC improvements

- [Corrected eth\_getLogs default fromBlock value](https://github.com/hyperledger/besu/pull/4513)
- [Remove 'publicKey' and 'raw' from Transaction RPC API response](https://github.com/hyperledger/besu/pull/4575)
- [Added max range CLI option for eth\_getLogs](https://github.com/hyperledger/besu/pull/4597)
- [RPC parameter error improvements. Test updates](https://github.com/hyperledger/besu/pull/4510)

Logging improvements

- [Changed chain download error log level from error to debug](https://github.com/hyperledger/besu/pull/4775)
- [Reduced logging level on Subscriber error callback](https://github.com/hyperledger/besu/pull/4485)

Bugfixes

- [RLP zero encoding fix](https://github.com/hyperledger/besu/pull/4388)

### Maintainer github handle: Gabriel-Trintinalia

Is Besu Maintainer? Yes

Query for mainnet label on merged PRs: [https://github.com/hyperledger/besu/pulls?q=+is:pr+author:Gabriel-Trintinalia+closed:>2022-07-01+label:mainnet](https://github.com/hyperledger/besu/pulls?q=+is%3Apr+author%3AGabriel-Trintinalia+closed%3A%3E2022-07-01+label%3Amainnet)

Details on mainnet contributions:

Withdrawals:

- [Initial implementation of EngineGetPayloadV2](https://github.com/hyperledger/besu/pull/4833)

RPC improvements:

- [Add accessList field to Transaction Call Object](https://github.com/hyperledger/besu/pull/4802)
- [Add type field to eth\_getTransactionReceipt](https://github.com/hyperledger/besu/pull/4713)
- [Fix storage key format for eth\_getProof](https://github.com/hyperledger/besu/pull/4564)

Eth Protocol

- [Implement eth/68 (EIP-5793)](https://github.com/hyperledger/besu/pull/4730)
- [Implement eth/67 sub protocol (EIP-4938)](https://github.com/hyperledger/besu/pull/4646)

Bug fixes

- [Fix attempt to send unsupported message (13) via cap eth/67](https://github.com/hyperledger/besu/pull/4732)
- [Fix ConcurrentModificationException on ReattemptPendingPeerRequests](https://github.com/hyperledger/besu/pull/4206)
- [Improve pending blocks retrieval mechanism](https://github.com/hyperledger/besu/pull/4227)

...