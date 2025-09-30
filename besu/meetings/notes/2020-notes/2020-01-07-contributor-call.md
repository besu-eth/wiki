# 2020-01-07 Contributor Call

Meeting Video: [https://consensys.zoom.us/rec/play/6JYtd-D9\_Tk3E93HtQSDVvF9W46\_KqOshnNL-adenR6yBXcHOgWhYLIRM7c\_stvozSqZr1YS4m-ien2J?autoplay=true](https://consensys.zoom.us/rec/play/6JYtd-D9_Tk3E93HtQSDVvF9W46_KqOshnNL-adenR6yBXcHOgWhYLIRM7c_stvozSqZr1YS4m-ien2J?autoplay=true)

Housekeeping

General Announcements

Release Updates

  

Conferences:

- EthDenver
- EthCC
- Global Forum

Releases:

- The current plan is the one discussed on last call, with 1.4 beta releases
- 1.40 targeted at 27 Feb 2020

Work updates:

- ETH Classic fork sometime next week, make sure to upgrade to latest version of Besu if running a classic node
- Caliper’s updates coming starting tomorrow

Other Business:

- Besu Consensus Failure: Full post mortem found on the [Besu wiki](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Mainnet+Consensus+Bug+Identified+and+Resolved+in+Hyperledger+Besu)
- Parity Attack: 
- Valid block header, yet invalid block values in body that didn’t match the headers
- Parity was caching the block and therefore wouldn’t accept valid versions of the block
- Besu and Geth weren’t affected by this attack
- Muir hard fork went pretty well

Open Forum:

- Lacchain rep wasn’t present, item skipped
- Open Contributor Questions:
  - Helped resolve Aditya's question about [https://jira.hyperledger.org/browse/BESU-52](https://jira.hyperledger.org/browse/BESU-52)