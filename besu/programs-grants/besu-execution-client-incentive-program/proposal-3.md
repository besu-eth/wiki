# Proposal #3

- [Guiding Principles](#guiding-principles)
- [Processes](#processes)
  - [Operator:](#operator)
  - [Key Management](#key-management)
- [Transaction Fees & Validator Rewards Funds Distribution](#transaction-fees-validator-rewards-funds-distribution)
  - [Operator Pool](#operator-pool)
  - [Hyperledger Pool](#hyperledger-pool)
  - [Patronage Pool](#patronage-pool)
  - [Ethereum Mainnet Development](#ethereum-mainnet-development)
- [Distribution of Withdrawal Keys](#distribution-of-withdrawal-keys)
  - [Proportional Distribution of Keys](#proportional-distribution-of-keys)
  - [Liquidation and Impact to Patronage Pool](#liquidation-and-impact-to-patronage-pool)
- [Exhibit A](#exhibit-a)

## **Guiding Principles**

1. Per the Program’s [Terms](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Besu+Execution+Client+Incentive+Program), the Ethereum Foundation has the right to change and/or update the program at any point. That is, the Ethereum Foundation acts as a check and balance that ConsenSys and the Hyperledger Foundation continue to meet the requirements of the program. 
2. This program offers client teams ETH-denominated rewards which unlock over time, as long as they continue to build software which meets the performance and security requirements of mainnet. There are two types of rewards that will be granted: 
3. Transaction and Validator Fees
4. Withdrawal Key Funds 
5. The Ethereum Foundation will only provide future organizations who have demonstrated long term support for Besu's mainnet work access to the principal capital of the program. To date, these organizations are ConsenSys and HLF. If future organizations want to be considered, the EF and HLF can agree to add them to the program. 
6. Any funds that are directed to ConsenSys, ConsenSys has sole discretion on how to spend those funds, assuming it is meeting the EF’s expectations of funds’ usage. Similarly, any funds that are directed to Hyperledger, Hyperledger has sole discretion on how to spend those funds, assuming it is meeting the EF’s expectations of funds’ usage. 

## **Processes**

### Operator:

ConsenSys will be the operator running the validator nodes in the near/medium term. The EF and HLF can make a decision on whether to change that structure at any point and invite a new party to also run the validator nodes. There will be 144 validator nodes included in this Program. 

### Key Management

There are three types of keys that are being managed in this process: Withdrawal Keys, Block Signing Keys and Transaction Fee Keys.

**Withdrawal Keys**

The Ethereum Foundation holds the withdrawal keys. The EF sends the withdrawal keys based on the proportions outlined in the “Distribution of Withdrawal Keys” section. The withdrawal keys have control over the validators’ principal and rewards upon withdrawal.

**Block Signing Keys**

These keys are used by the validator to attest to blocks. The organization with control over the validators holds the block signing keys.

**Transaction Fee Keys**

This key has control over the address where transaction fees are sent. This a regular Eth1 address. Unlike the other two keys, the Transaction Fee Keys can be updated easily.

## **Transaction Fees & Validator Rewards Funds Distribution**

The proceeds of the validators (i.e. transaction fees and rewards) will be split into three pools: 20% to the node operator, 20% to Hyperledger Foundation as a directed donation, and 60% to a patronage pool.  These funds will be distributed following the processes outlined above.

At the start of every vesting period, the transaction fees will be set up to be proportionally distributed based on prior 6 month’s contributions of maintainers. ConsenSys will automatically send their funds based on how the transaction fee keys are set up for that vesting period. Similarly, Hyperledger will receive their funds directly based on how the transaction fee keys are set up for that vesting period. This design is to get the transaction fees received to limit the tax exposure to both organizations. However, at the end of each vesting period, we can expect there will be a slight discretion on the fees received and the fees that were “over” sent to one party, will then be sent to the other party.

For example, at the beginning of a vesting period it is determined that ConsenSys receives 80% of fees and Hyperledger receives 20%. If at the end of that vesting period, the distribution is 75% with ConsenSys, 25% with Hyperledger, ConsenSys will send one transaction to Hyperledger’s address with the 5% of funds it owes to match the patronage pool allocation. 

*Exhibit A also demonstrated the breakdown for funds.*

### Operator Pool

20% of proceeds will go to the service provider operating the validator nodes. 

The node operator will provide access to the canary nodes to Hyperledger mainnet developers for development and debugging purposes.  Access to performance nodes may be restricted to node operations. There is an expectation that if a contributor requests access to the canary nodes, they will then be added to the respective monitoring channels for those nodes.

The service provider can be changed by the Ethereum Foundation and if they want to change the program.

The initial service provider will be ConsenSys or a fully owned subsidiary of ConsenSys.

### Hyperledger Pool

Hyperledger will receive or direct 20% of the proceeds. This pool will be a directed donation towards Hyperledger Besu mainnet work paying for items including but not limited to:

- Payment of services consumed by the Hyperledger Besu project, such as
- Continuous Integration,
- Cloud Hosting fees for development (i.e. testnet nodes)
- source code hosting,
- any other such services directly related to development of mainnet capabilities in Hyperledger Besu
- *Note: These costs are separate from any incurred by ConsenSys.*
- Sending maintainers to speak at and promote Hyperledger Besu at Hyperledger events (such as the Global Forum and Members Summit) and Ethereum Foundation events (such as DevCon and AllCoreDevs meetings)
- Posting Bounties for work on Hyperledger Besu mainnet or mainnet related work
- Spending that would directly promote interoperability with Besu Mainnet functionality 
- Other spending that would directly promote and improve Hyperledger Besu

### Patronage Pool

60% will go to employers of maintainers (or where the employer designates). Maintainers are the only parties eligible to receive funds as a part of the Patronage Pool. The Besu community will manage a list of maintainers who contribute to mainnet in a vesting period. If there is a discretion around a maintainer’s contribution to mainnet, that will be escalated to the EF and HLF staff to decide on whether they meet eligibility. Hyperledger Besu community will use the current process for maintainership to determine who becomes maintainers.

### **Ethereum Mainnet Development**

Ethereum mainnet development works includes (without limitation) contributions to features, performance, and stability required for Mainnet operation of the Besu client. This work includes supporting work necessarily deriving from this effort, such as build maintenance, code cleanup, documentation, test maintenance and development, etc. This includes work on EIPs and proposals in all core devs intended for mainnet deployment up until such a time as they are known to be excluded from mainnet deployment. (for example BLS-12 work still qualifies but alternative proof of work algorithms no longer count although they once did).

Excluded is work relating to Ethereum Classic development, GoQuorum compatibility, private transactions, private transaction enclaves, permissioning, etc. and supporting work deriving exclusively from these activities.

## **Distribution of Withdrawal Keys**

### Proportional Distribution of Keys

The Ethereum Foundation will only provide organizations who have demonstrated long term support for Besu's mainnet work access to the principal capital of the program. To date, these organizations are ConsenSys and HLF. 

The HLF funds received via the withdrawal keys will go directly to HLF. It will not be passed along to the non-ConsenSys maintainers.

Withdrawal keys will be sent proportionally to these organizations’ mainnet maintainers to Besu over the entirety of the incentive program by the Ethereum Foundation. The keys give each organization ownership over the principal (because you then have custody of the funds upon withdrawal). The EF only considers the funds “sent” to the organization when the EF sends the withdrawal key. The EF will send the contributions to ConsenSys or HLF based on the number of maintainers but will be accounted for on the rolling period as demonstrated in Exhibit A.

Validator rewards beyond the principal will be allocated similarly to the Transaction Fees in which there might have to be a transfer between ConsenSys and Hyperledger to account for the different contributions. One important difference between the Transaction Fees and Withdrawal credential allocation is that the share of the former will be based on each vesting period, while the allocation of the latter is based on the **number of mainnet maintainers** **over the entire program.**

### Liquidation and Impact to Patronage Pool

The EF releases the withdrawal credentials in the period (as identified in the contract under “[Milestones](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Besu+Execution+Client+Incentive+Program)”) in the proportional manner identified above. Once withdrawals are received by ConsenSys, ConsenSys can choose to liquidate. 

If ConsenSys chooses to liquidate based on the withdrawal (as proportional to the amount of contributions CS makes over the duration of the program,) ConsenSys will reduce their share of the remaining program’s pool for all maintainers. For example, if ConsenSys liquidates 10% of all validators, ConsenSys; share of the patronage pool will be reduced by 10% going forward. The extreme version is that ConsenSys liquidates all its validators but is then ineligible for Patronage funds from the remaining validators.

Similarly, withdrawals received to HLF can decide on liquidation practices separately. ConsenSys will not have a say in how HLF liquidates its validators, even if the supermajority of maintainers are employed by ConsenSys.

## **Exhibit A**

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| **Vesting Period** | **ConsenSys (CS) Maintainers** | **Non-CS HLF Maintainers** | **Validator Rewards & Transaction Fee Share** | **Withdrawal Credential Share** |
| 1   | 8   | 2   | 80% CS / 20 % HLF \* | 80% CS / 20% HLF |
| 2   | 8   | 4   | 66% CS / 34% HLF \* | 72% CS / 28% HLF |
| 3   | 8   | 2   | 80% CS / 20 % HLF \* | 75% CS / 25% HLF |