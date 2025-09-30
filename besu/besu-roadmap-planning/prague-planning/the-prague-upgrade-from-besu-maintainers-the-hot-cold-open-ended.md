# The Prague Upgrade from Besu Maintainers - The Hot, Cold,  & Open-Ended

```
Written by the Besu Maintainers.  
  

```

To streamline Prague planning from the Besu client team, our maintainers propose the following scope...

***[Prague Meta-Thread](https://ethereum-magicians.org/t/pectra-network-upgrade-meta-thread/16809)***

# In-Favor

## EOF

Besu advocates for adding EOF to the Prague hard fork. 

The EVM Object Format is a collection of smaller changes aiming at paying down a significant amount of technical debt that the EVM has accrued over nearly a decade, and prepare the EVM so that "calcification" can occur on a robust foundation. EOF does not fundamentally change the execution of the EVM, instead it introduces a container format and migrates key instructions to new formats that resolve long standing problems such as eliminating dynamic jumps and the associated JUMPDEST analysis. Generally speaking there are four major themes addressed

1. Making EVM code O(n) to JIT and AOT compile  
2. Eliminating Code Introspection   
3. Eliminating Gas Introspection   
4. Make “Quality of Life” improvements easier

The last bullet point enables features in future forks and L2 usages of the evm. L2s can more safely perform wholesale changes to their gas schedule. Experimental and non-conforming EVM features (such as new opcodes) can be signaled with extra header fields. And because JUMPDEST analysis has been replace with deploy time code validation the contract size limit could be safely increased or even uncapped. Team Ipsolon has launched [https://evmobjectformat.org/](https://evmobjectformat.org/) for a more comprehensive list of features. 

Besu's implementation of EOF is nearly complete, awaiting the finalization of a few final details.

## EOAs, AA, & Next Steps

- [EIP-3074](https://eips.ethereum.org/EIPS/eip-3074) \- AUTH and AUTHCALL

Besu supports adoption of EIP-3074

This EIP was [considered and rejected](https://github.com/ethereum/pm/blob/13738d97baac05d2e6688225063fedb9d6ad54aa/AllCoreDevs-EL-Meetings/Meeting%20111.md?plain=1#L32) for the London hard fork, almost three years ago, citing security issues. There was a call for a security audit at the time, which has not been done. The EIP would benefit from such an assessment. A major recent update to the nonce handling rules allows for a user to revoke authorizations with a single action. This recent specification change has removed the major safety concerns team members have had.

The Besu team views the need for 3074 as an opportunity cost. If we do not ship something in Prague, we run the risk of not supporting AA for the next 2-3 years. While this necessarily creates complexity in censorship resistance workstreams, the learnings from implementing AA sooner will allow us to have a better, more informed design where AA transaction validation logic is baked-in. This is a feature, not a bug. Keeping UX on Ethereum stunted for 2-3 years in order to solve some niche MEV challenges via ePBS seems like a poor trade-off. 

  

- [EIP-7553: Separated Payer Transaction](https://eips.ethereum.org/EIPS/eip-7553)
  - Another tool to help enhance EOA UX, easy to reason about and implement new TX types and test 

## Supported Grab-Bag EIPs 

- [EIP-2935: Save historical block hashes in state 2](https://eips.ethereum.org/EIPS/eip-2935)
  - Implemented, not complex, brings value after Verkle. Shipping this in Prague will allow us to simplify Osaka for Verkle. 
- [EIP-2537](https://ethereum-magicians.org/t/eip-2537-bls12-precompile-discussion-thread/4187/48) - BLS Precompile
- [EIP-7212](https://eips.ethereum.org/EIPS/eip-7212) \- Precompile for Secp256R1 
  - Besu team to run Benchmarks and help with understanding libraries, gas costing, and existing tooling
- [EIP-7623: Increase calldata cost](https://eips.ethereum.org/EIPS/eip-7623)
  - Happy with costing changes, smaller blocks, lower latency/state, chain ops 
  - Small implementation in the EL

# Neutral/No Opinion

- [EIP-7664: Access-Key opcode](https://github.com/ethereum/EIPs/pull/8357)
  - Could be significant EVM work. Do we have an alternative? 
  - Not sure of necessity 
  - Might provide better security UX 
- [EIP-7557: Block-level Warming](https://eips.ethereum.org/EIPS/eip-7557)
  - Need to better understand the code complexity 
  - Might add complexity to the state DB that may add more data, memory, etc. Need to understand the impact to our code. 
- [EIP-7377: Migration Transaction](https://eips.ethereum.org/EIPS/eip-7377)
  - Good migration path for AA, but not instead of an encompassing AA solution like 3074 

  

- [EIP-7545: Verkle proof verification precompile 1](https://eips.ethereum.org/EIPS/eip-7545)
- [EIP-7609: Decrease TLOAD/TSTORE pricing for common cases 1](https://eips.ethereum.org/EIPS/eip-7609)
- [EIP-3068: Precompile for BN256 HashToCurve Algorithms](https://eips.ethereum.org/EIPS/eip-3068)

# Opposed

## SSZ

- [EIP-6404: SSZ Transactions Root 18](https://eips.ethereum.org/EIPS/eip-6404)
- [EIP-6465: SSZ Withdrawals Root 9](https://eips.ethereum.org/EIPS/eip-6465)
- [EIP-6466: SSZ Receipts Root 7](https://eips.ethereum.org/EIPS/eip-6466)
- [EIP-6493: SSZ Transaction Signature Scheme](https://eips.ethereum.org/EIPS/eip-6493)

Aesthetics and consistency with the CL is not necessarily a reason to engage on a large bucket of work on the EL. 

## Opposed Grab Bag EIPs 

- [EIP-6913: SETCODE instruction](https://eips.ethereum.org/EIPS/eip-6913)
  - Code immutability is questionable. 
- [EIP-5806](https://eips.ethereum.org/EIPS/eip-5806) Delegate Transaction
- Weakly Opposed - [EIP-5920: PAY opcode 1](https://eips.ethereum.org/EIPS/eip-5920)
  - Might break some assumptions of existing smart contracts 
  - Ether can get stuck in a smart contract that cannot send it 
  - Users may create issues with stuck Ether and