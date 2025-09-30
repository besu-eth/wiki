# Switchable Consensus Parameters

# Real World Use Case

A single member of an IBFT Blockchain consortium wishes to leave the group, but wants to maintain their existing data.

Thus - a mechanism must exist which allows the list of validators to be overridden with a hard-coded list at a given block.

# Required Changes

The overall goal of this change is that the validators for an IBFT2 network change at a given block - what this means:

- The genesis file must specify block at which the validators are to change, and also who the new validators are
  - It *must*  list the new validators, not just the expected extra data, as the new validators are required to know that at block-X they are  
responsible for producing a block (this is different to existing behaviour as the genesis file defines the block upon which all work is to be  
performed - this change defines the block to be *created).*
- IBFT business logic must be able to determine the currently active validators from a source other than *just*  the latest block - i.e. it must somehow  
factor in the "validator switch" data specified in the genesis file
- Block Validator rules must be updated to expect the validators in the block to be either as per existing voting, OR as per genesis file content
  - This will *probably*  be abstracted behind the VoteTallyCache
- Votes cast prior to the "change Block" will need to be discarded on a change into a custom fork

# Items to Consider

Currently, the overarching behaviour of the system is defined by the ProtocolSchedule and the associated ProtocolContext. the validators and votes are (indirectly) contained within the ProtocolContext, of which  
only 1 exists for the lifetime of the network.  
It is proposed that ConsensusState contained with the ProtocolContext be either:

- Replaceable upon custom block
- Entire ProtocolContext be overwritten upon custom block

# Approach

The existing forking process (in the ProtocolSchedule) is to be reused - however, the forks/milestones will be recognised as "transitions" in the genesis file.

**Genesis File**

```
{
  "config": {
    "chainId": 4,
    "homesteadBlock": 1,
    "eip150Block": 200,
    "eip150Hash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "eip155Block": 300,
    "eip158Block": 300,
    "byzantiumBlock": 400,
    "transitions" : {
      "250" : {
        "ibft2": {
          "validators": ["0x12345...", "0x09875..."],
        }
      },
      "350": {
        "ibft2": {
          "validators": ["0x12345...", "0x09875..."],
        }
      },
    },
  },
...
```

During construction of the ProtocolSchedule additional ProtocolSpecs will be added at the "transitions" block numbers, these