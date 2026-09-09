# Hegotá EIP Selection — Explainer

This page walks through our team's tier ranking of the execution-layer (EL) EIPs proposed for **Hegotá**. It's meant as a reference for anyone who wasn't in the room when we ranked these, not a line-by-line rationale for all 37 EIPs.

Our full ranking is viewable on [Forkcast](https://forkcast.org/rank/#r=S:5920,7668,7906,8250,8253,8355,8368;A:3298,7709,4758,7666,7862,8131,8151,8279;B:7979,8077,8163,8272,8374;C:2488,7807,7819,7851,7923,8115,8116,8188,8200,8298,8372;D:7645,8094,8182,8219,8304,8358)

Thematically: 


We lean hard into 8141 and its extensions, and cleanup techdebt.

## S tier — must ship

| EIP | Name | Why it's here |
|---|---|---|
| [5920](https://eips.ethereum.org/EIPS/eip-5920) | PAY Opcode | Small, low-surface addition that closes a long-standing gap: sending value without invoking recipient code. |
| [7668](https://eips.ethereum.org/EIPS/eip-7668) | Remove Bloom Filters | Cleans up a receipt/logs mechanism that's largely obsolete now that clients index logs differently. |
| [7906](https://eips.ethereum.org/EIPS/eip-7906) | Part of the Frames extension package alongside EIP-8298 and EIP-8151. We think frames extensions make sense to ship for immediate use with EIP-8141|
| [8250](https://eips.ethereum.org/EIPS/eip-8250) | Keyed Nonces for Frame Transactions | Frames-core support. |
| [8253](https://eips.ethereum.org/EIPS/eip-8253) | Bump Nonce of Zero-Nonce Storage Accounts | State-transition cleanup that meaningfully simplifies the upcoming trie migration. Pays down techdebt|
| [8355](https://eips.ethereum.org/EIPS/eip-8355) | ML-DSA Verification Precompiles | Post-quantum work needs to start ASAP. |
| [8368](https://eips.ethereum.org/EIPS/eip-8368) | CPSB Recalibration for New Gas Limit | Recalibrates cumulative pricing/state-bloat controls for the new gas limit set by Glamsterdam. |

## A tier — high priority, please ship

| EIP | Name | Why it's here |
|---|---|---|
| [3298](https://eips.ethereum.org/EIPS/eip-3298) | Removal of Refunds | Deletes an entire class of gas-refund metering edge cases the last fork paid for dearly. |
| [4758](https://eips.ethereum.org/EIPS/eip-4758) | Deactivate SELFDESTRUCT | Removes the last live `SELFDESTRUCT` path — a testing hazard every future EIP otherwise has to define behavior against. Techdebt pay down. |
| [7666](https://eips.ethereum.org/EIPS/eip-7666) | EVM-ify the Identity Precompile | Rewrites the identity precompile as EVM bytecode instead of native client code — a proof point for EVMification (EIP-8200). We like this one because it is simple, and a useful proof of concept. |
| [7862](https://eips.ethereum.org/EIPS/eip-7862) | Delayed State Root | Easy to implement, performance improvement. |
| [8131](https://eips.ethereum.org/EIPS/eip-8131) | Unified Transaction Content Floor | Bounds worst-case calldata pricing; pairs with EIP-8279 as the other half of the bounding work. |
| [8151](https://eips.ethereum.org/EIPS/eip-8151) | Account Code Restricted ecRecover | Valuable Post-Quantum work|
| [8279](https://eips.ethereum.org/EIPS/eip-8279) | Block Access List Byte Floor | Floors adversarial Block Access List pricing so worst-case block construction stays bounded. |
| [7709](https://eips.ethereum.org/EIPS/eip-7709) | Read BLOCKHASH from Storage and Update Cost | zkVM witnesses benefit from this, reducing their size significantly |

## B tier — on the bubble

| EIP | Name | Why it's here |
|---|---|---|
| [7979](https://eips.ethereum.org/EIPS/eip-7979) | Call and Return Opcodes for the EVM | Adds new control-flow opcodes; reasonable, but adds surface to a fork already carrying two headliners worth of interaction testing. |
| [8077](https://eips.ethereum.org/EIPS/eip-8077) | eth/XX: Announce Transactions with Nonce | Richer mempool announcements for the Frames era; needs sophisticated network simulation. |
| [8163](https://eips.ethereum.org/EIPS/eip-8163) | Reserve EXTENSION (0xae) Opcode | A reservation with no committed consumer yet — can ride a later fork. |
| [8272](https://eips.ethereum.org/EIPS/eip-8272) | Recent Roots for Frame Transactions | Frames-core: lets private transactions reference recent on-chain state in an attester-verifiable form. |
| [8374](https://eips.ethereum.org/EIPS/eip-8374) | Persist Warm Access Sets Across Reverts | Net-metering repricing; paired with EIP-8358 and shouldn't carry a different grade than it does. |

## C tier — not disqualified, but ehhhhhhhh

| EIP | Name | Why it's here |
|---|---|---|
| [2488](https://eips.ethereum.org/EIPS/eip-2488) | Deprecate the CALLCODE Opcode | Low urgency. |
| [7807](https://eips.ethereum.org/EIPS/eip-7807) | SSZ Execution Blocks | Wide-blast-radius formatting migration with no Hegotá-specific dependency forcing it now. |
| [7819](https://eips.ethereum.org/EIPS/eip-7819) | SETDELEGATE Instruction | |
| [7851](https://eips.ethereum.org/EIPS/eip-7851) | Code-Controlled EOA Delegation |  |
| [7923](https://eips.ethereum.org/EIPS/eip-7923) | Linear, Page-Based Memory Costing | Repricing-family change; it's good, we like it, not sure the value yield is there |
| [8115](https://eips.ethereum.org/EIPS/eip-8115) | Batch Priority Fees at End of Block | Same repricing-churn concern as 7923. |
| [8116](https://eips.ethereum.org/EIPS/eip-8116) | Replace Cumulative Receipt Fields | performance yield is low, but it's good tech-debt cleanup. |
| [8188](https://eips.ethereum.org/EIPS/eip-8188) | Last-Written Block for Accounts and Slots |  |
| [8200](https://eips.ethereum.org/EIPS/eip-8200) | EVMification | We like EVMification as a direction, but flagged this one as feeling premature — every replacement bytecode needs an exact-behavior audit, is it fast enough at runtime? |
| [8298](https://eips.ethereum.org/EIPS/eip-8298) | SETCODEFROM Code Reuse Instruction |  |
| [8372](https://eips.ethereum.org/EIPS/eip-8372) | Normalized State Gas Limit |  |

## D tier — declined for inclusion

| EIP | Name | Why it's here |
|---|---|---|
| [7645](https://eips.ethereum.org/EIPS/eip-7645) | Alias ORIGIN to SENDER | Breaks assumptions baked into deployed contracts for no offsetting security gain. |
| [8094](https://eips.ethereum.org/EIPS/eip-8094) | eth/vhash: Blob-Aware Mempool |  we questioned why this needs a fork at all if a sparse blobpool already captures most of the benefit. |
| [8182](https://eips.ethereum.org/EIPS/eip-8182) | Private ETH and ERC-20 Transfers | Enshrines one specific privacy mechanism at the protocol layer; the Frames-based path gets similar outcomes with less protocol surface and keeps schemes competing. |
| [8219](https://eips.ethereum.org/EIPS/eip-8219) | Checked Arithmetic Opcodes | Good idea, compiler teams can already pursue, not urgent |
| [8304](https://eips.ethereum.org/EIPS/eip-8304) | Trustless Log and Transaction Index |  |
| [8358](https://eips.ethereum.org/EIPS/eip-8358) | Net Gas Metering for Account Changes |  |

## Open questions to close out

A few items above still need an answer before we'd call this ranking final:

- **EIP-2488**: has anyone actually verified the deprecation justification, or is it still an unvalidated claim?
- **EIP-8200 / EIP-7666 (EVMification)**: we're supportive of the direction, but what stops the EVM-ified precompiles from just getting optimized back into native precompiles later.
- **EIP-8094**: the bandwidth/mempool savings case hasn't been made convincingly enough to justify a fork-scoped change, especially with sparse blobpool already helping here.


