# Refactor EVM into a stand alone library

Status: Proposed

# EVM Library 

## Feature Overview: 

Pull out the EVM functionality from the \`core\` subproject/module into a separate \`evm\` subproject module, suitable for use as a library component. Limited to no classes unrelated to EVM functionality will be required for the dependency (example: no QBFT, no ETCHash, no transaction type code, etc).

## Rationale

Besu is currently monolithic in its deployment.  While there is some component and package separation those are mostly accidental and reflect boundaries between developer groups.  There are a number of components that may be severable with effort (EVM, consensus, p2p, rpc, network definitions, etc).  The EVM is fairly self contained and would be a good starting point to start this process.

## Potential Risks / Rabbit Holes: 

- Deep code changes may be required

## In Scope:

- no measurable performance regressions for mainnet and existing public networks
- Usable by other projects
  - Usable by Web3j in their local EVM execution tasks
  - Includable in other DLTs (or Layer 2s) without requiring full mainnet semantics
  - Includable in Android applications without large library dependencies
- Ultimately move to a top-level repo as a Besu subproject.
  - Within Besu either included via submodule reference or via synchronized releases.
- To the extent possible testable with existing Ethereum reference tests (via t8n tool interfaces)

## Out of scope:

- Pluggable EVM/Contract layer.
  - May be a good idea, but not now.

## Longer description: 

Anticipated Changes

- Create appropriate Interface classes for use by Besu to access the EVM component
  - Pretty much anything Mainnet\* is a candidate here
- move code to new directory/repository
- rework build scripts to support new locations

Targets of Opportunity:

- re-implement EVM Tool to just the EVM library
- support t8n tool formats
- Quarkus/GraalVM AOT build (suitable for fuzz testing)
- publish library to maven central

## Task List of Changes:

- Use the o.h.b.plugin.data classes instead of the o.h.b.core classes
  - The o.h.b.core classes that need it will all gain a `fromPlugin` method if they don't have it already
- Change `BlockHashLookup` parameters & such to `Function<Long, Hash>`
- Remove blockchain reference (only needed for BlockHashLookup)
- Add `setContextVar`/ `getContextVar` methods and move Privacy things there.
  - isPersistingPrivateState
  - getPrivateStateMetadataUpdater
  - transaction
  - transactionHash (pmtHash)
- Move to Tuweni Wei
- Move `Gas` from Core to EVM
- Factor out transaction wrapper gas calculations into a new BlockchainGasCalculator
  - Extracting access lists and intrinsic costs of TX
  - code deposit cost
  - max pmt cost
- Create in EVM world state updater interface
- Remove uses of account and delegate to the storage interface
  - add method to test if an account isEmpty
  - for an address get current storage value
  - for an address get original storage value
- create EVM focused blockheader interface (to support operations), possibly add to o.h.b.plugin.data
  - basefee
  - blockhash (?)
  - difficulty
  - gaslimit
  - block number
  - block timestamp
- Move account "warm-up" out of the EVM into MainnetTransactionProcessor
  - Not the tracking of warm addresses/slots, but the actual reading from the DB
- Remove contract versioning