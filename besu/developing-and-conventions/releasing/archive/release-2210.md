# Release 22.1.0

RC3 was done from main

RC4 was just the besu-native fix

So the only other things we would need to cherry pick would be bug fixes. 

Branch to cherry pick things to [https://github.com/hyperledger/besu/tree/release-22.1.0-RCx](https://github.com/hyperledger/besu/tree/release-22.1.0-RCx)

## Regressions since 21.10.x:

- [ ] web socket streaming - was introduced in RC2
  - [ ] max frame size [https://github.com/hyperledger/besu/pull/3386](https://github.com/hyperledger/besu/pull/3386)
  - [ ] WS close stream [https://github.com/hyperledger/besu/pull/3399](https://github.com/hyperledger/besu/pull/3399)
  - [ ] Improve closing behavior of JsonResponseStreamer [https://github.com/hyperledger/besu/pull/3421](https://github.com/hyperledger/besu/pull/3421)

## Other bug fixes:

- [ ] EC curve param added public key export/export-address subcommands [https://github.com/hyperledger/besu/pull/3333](https://github.com/hyperledger/besu/pull/3333)
- [ ] the peering fixes:
  - [ ] prevent peering with yourself [https://github.com/hyperledger/besu/pull/3342](https://github.com/hyperledger/besu/pull/3342)
  - [ ] Chain download failed due to IndexOutOfBoundsException in PipelineChainDownloader PR [https://github.com/hyperledger/besu/pull/3326](https://github.com/hyperledger/besu/pull/3326)
- [ ] the sync fixes:
  - [ ] Disable RocksDB TTL compaction [https://github.com/hyperledger/besu/pull/3356](https://github.com/hyperledger/besu/pull/3356)
  - [ ] ~Refactor to async retrieve blocks, and change peer when retrying to get a block [https://github.com/hyperledger/besu/pull/3326](https://github.com/hyperledger/besu/pull/3326)~  
- [ ] Fix launcher [https://github.com/hyperledger/besu/pull/3352](https://github.com/hyperledger/besu/pull/3352)
- [ ] Handle NPE forkId [https://github.com/hyperledger/besu/pull/3409](https://github.com/hyperledger/besu/pull/3409)
- [ ] Then 3326 used Slf4jLambdaHelper so we backported that manually
- [ ] change logging level for invalid transaction from WARN to DEBUG (goerli validator is periodically getting spammed) [https://github.com/hyperledger/besu/pull/3416](https://github.com/hyperledger/besu/pull/3416)

See PR [https://github.com/hyperledger/besu/pull/3442](https://github.com/hyperledger/besu/pull/3442)