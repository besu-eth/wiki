# Change to Besu Defaults - Q1 2024

# 2024 Besu Defaults

# Context

Currently starting Besu without configuring a handful of options will create a sub-par experience for users. It will use FOREST and FAST sync and attempt to connect to Ethereum Mainnet. These options are no longer suitable for Mainnet and Proof of stake.

For private network users, configuration must be done either way to set up a custom genesis, chain ID, and to configure connections to peers. Defaults will have less impact on these users. Enterprises and developers are more likely to read the documentation prior to first start up.

# Suggestions

The Consensys team is suggesting a re-evaluation of defaults in the new year. We are also simultaneously suggesting adding “profiles” to Besu that when set, provide defaults that serve certain use-cases or sets of users. 

One more note. When setting a profile, any other options the user configures that fall underneath that profile will be overwritten. For example, if a user sets `--profile=enterprise` and `--sync-mode=FULL` it will override the sync mode flag from `FAST`  to `FULL`.

## Defaults, no profile

When starting up Besu with no additional commands `./bin/besu` , the following defaults are suggested:

- Sync Mode: SNAP
- Data-storage-format: BONSAI
  - Full flat DB by default **`Xsnapsync-synchronizer-flat-db-healing-enabled=true (DELETE THIS FLAG → Safety concerns [Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence))`** 
  - Full flat DB will be default for all BONSAI users
  - bonsai-limit-trie-logs-enabled=True
  - bonsai-historical-block-limit=512
- Network: Mainnet (should we specify a testnet for first time users without a config?)
- Max-peers: 50 (in line with Geth and other clients)
- \-Xp2p-peer-lower-bound=25
- Tx-pool: Layered (already default)

These defaults promote the most performant profile for public networks with the full chain history. This is especially important when we ship SnapSync as a Server in Q1. We want these users to be able to serve any data required by peers to be good network citizens. We also want to bump the peer count to enable more robust peering and serving more data to the network.

## Profile Defaults

The Consensys Team is suggesting 4 profiles with their own defaults:

- Selfish-staker
- Considerate-staker (name?)
- Private-network / Enterprise (?)
- RPC Provider
  - Archive - Awaiting Bonsai Archive to change defaults
  - Near-head - Standard full node

Broken down below are the profiles.

### Selfish-staker

- Sync mode: CHECKPOINT
  - Lowest disk, quickest sync, cannot serve old block data, can serve all world state data
- Data-storage-format: BONSAI
  - bonsai-historical-block-limit: 128
- Max-peers: 25 
  - Slight reduction in CPU overhead from peering
  - \-Xp2p-peer-lower-bound=10
- Chain-pruning: Enabled
  - Deposit logs / tree dependency (TEKU ONLY) 

### Considerate-staker

- Sync mode: SNAP
  - More disk, quickest sync, can serve more block data, can serve all world state data
- Data-storage-format: BONSAI

### Private-network / Enterprise (?)

- Sync-mode: FAST (move to snap —> not until snap server and Bonsai are tested in this environment, might require bonsai archive for some networks to migrate entirely over)
  - `--fast-sync-min-peers` = 3
- Min-gas-price=0?
- `--remote-connections-limit-enabled=false`
- Tx-pool=Legacy / Sequential
  - `--tx-pool-no-local-priority` 
  - \--tx-pool-limit-by-account-percentage=(something bigger than 4 transactions)

### ~RPC Provider (Needed?)~

- **Archive** - Awaiting Bonsai Archive to change defaults, then…
  - data-storage-format: Bonsai
  - New options for how many checkpoints to take (i.e. tradeoff between storage and rollback time)
- **Near-head** - Standard full node
  - Uses default profile from above

Both types:

- revert-reason=true
- rpc-gascap? (currently 1 eth, may want to lower for RPC providers)