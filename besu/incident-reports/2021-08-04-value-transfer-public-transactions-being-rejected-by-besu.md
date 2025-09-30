# 2021-08-04 Value transfer public transactions being rejected by Besu

## Incident Summary

  

A user [reported a bug](https://github.com/hyperledger/besu/issues/2606) saying that Besu was considering public transactions as if they were private transactions. Because of that, they were not able to send transfer value transactions to their Besu nodes.

A few hours later we identified the problem and we [created a PR](https://github.com/hyperledger/besu/pull/2609) with the fix.

We coordinated a hotfix release version 21.7.2. This new version will be the new recommended version for the London hard fork.

## Leadup

The bug was introduced by [this commit](https://github.com/hyperledger/besu/commit/974f58848d4bfef51b5192061752dd31f2f07f3f#diff-caf924b8f77d2f58d1541a1d50f97973799ee947f0b8545e36fa40bd84c1b964) on 10th Jun 2021. Because this wouldn’t impact a majority of users, we didn’t hear anything about it until the 4th of August.

This bug affects versions: 21.7.0-RC1, 21.7.0-RC2, 21.7.0 and 21.7.1.

First, we thought the problem wasn’t impacting users. But later we identified that the change in the TransactionPool would cause issues for value transfer public transactions.

## Problem

The scope of this problem is limited to:

- Value transfer public transactions received via JSON-RPC
- Value transfer public transactions received via DevP2P

When receiving a value transfer tx via JSON-RPC, Besu was considering it a private tx and enforcing a validity check that prevents private transactions from transferring value. That's why it was returning the error message ether value is not supported for private transactions.

When receiving value transfer tx via DevP2P, Besu was considering those transactions invalid, not propagating them further.

Luckily, the logic for block validation and import wasn't using the same code path. This means that Besu would still successfully synchronise with Mainnet and be up-to-date. **This bug won't cause a fork**.

It is worth mentioning that this bug was caused by a specific combination of factors, related to the chainId value being 1. Unfortunately, our tests do not cover scenarios with specific chainIds.

## Impact

The impact wasn’t major as we were not causing a fork in the network. However, users were not able to send transfer transactions through their Besu nodes. We don’t have an estimate of how many users were impacted by this problem.

Regarding the transactions propagation, because other nodes in the network would also propagate the same transactions, the impact of Besu not propagating them is low.

## Actions

- To prevent something like this from happening again, we have added a test that validates that transactions with chainId = 1 (and any other chainId) won't be affected by private transaction logic.
- A hotfix version 21.7.2 will be released containing the fix.

## Next Steps

- We will [review](https://github.com/hyperledger/besu/issues/2613) the branching of execution of public vs private transactions in an effort to better isolate their differences. The ideal scenario would be that, when running on public networks, none of the private tx logic would be ever in the code execution path.