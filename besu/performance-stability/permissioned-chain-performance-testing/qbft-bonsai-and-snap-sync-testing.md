# QBFT, Bonsai, and Snap-Sync testing

**Update:** PR [https://github.com/hyperledger/besu/pull/7140](https://github.com/hyperledger/besu/pull/7140) now merged and adds working experimental support for QBFT + Bonsai + Snap sync

  

Previous notes below:

Prior to being able to recommend Bonsai and/or snap sync for permissioned chains work is needed to make the combination of QBFT, Bonsai, and snap-sync work reliably.

Summary of PRs related to this work:

1. [https://github.com/hyperledger/besu/pull/7204](https://github.com/hyperledger/besu/pull/7204) (merged to main) - prevents persisting of proposed blocks to ensure only committed blocks are persisted to world state
2. [https://github.com/hyperledger/besu/pull/7140](https://github.com/hyperledger/besu/pull/7140) (WIP) - adds an experimental flag to enable QBFT + snap sync. Quits snap-sync early when a new chain scenario is detected.

Issues seen before now when Bonsai and/or snap-sync is used with QBFT:

- [https://github.com/hyperledger/besu/issues/6680](https://github.com/hyperledger/besu/issues/6680)
- [https://github.com/hyperledger/besu/issues/6053](https://github.com/hyperledger/besu/issues/6053)

For those working on this feature, the tar file below can be used to run a 4-validator QBFT chain for testing. The 4th node has `Xsynchronizer-world-state-request-parallelism=1` set as without this, the account data range requests fail to all be marked as complete.

  

[4-validator-dir.tar.gz](./attachments/4-validator-dir.tar.gz)

>