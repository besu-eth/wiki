# Maximum Validator count for an IBFT2 Network

### Summary

We did some tests on the maximum number of validators in a network under various networking scenarios with light load. Results showed **30** to be safe under light load; beyond that you could experience degradation of performance and may stall the network. This is also dependant on the smart contracts that are in use on your network - the heavier and complex they are, you should reduce the max validators and we recommend you test this out prior to production.

### Test Setup

- Besu 21.10.0
- IBFT2 consensus algorithm - Block time 5s
- AWS - t3.large instances 2Cpu 8G
- No privacy
- Test contract we used: [https://github.com/ConsenSys/quorum-dev-quickstart/blob/master/files/common/smart\_contracts/contracts/SimpleStorage.sol](https://github.com/ConsenSys/quorum-dev-quickstart/blob/master/files/common/smart_contracts/contracts/SimpleStorage.sol)   

### Assumptions

- Even distribution of traffic 
- No private tnxs testing performed

### Tests

#### Test1: Single Region with instances spread across 3 AZs; routing done internally on private IPs  

Upto 36 validators were fine and no loss of performance. Beyond 32 validators, block times rose 0.5s

#### Test2: Across 3 Regions (Ohio, Paris, Sydney) with instances spread across 3 AZs in each region. VPCs were peered and routing was done internally on private IPs

Upto 36 validators were fine and no loss of performance. Beyond 32 validators, block times rose 0.5s. At 36 validators and sustained load (5min+) the transaction pool started to grow exponentially 

#### Test3: Across 3 Regions (Ohio, Paris, Sydney) with instances spread across 3 AZs in each region. Routing was done on the public internet and on public IPs

Upto 30 validators were fine and no major loss of performance. At 30 validators the transaction pool started to grow a bit, and block times went up 0.2s. 

At 35-38 validators, sustained load (5min+) saw the tx pool time grow and then halted the network at 38 validators