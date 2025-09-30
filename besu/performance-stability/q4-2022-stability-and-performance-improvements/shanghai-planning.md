# Shanghai planning

[https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/shanghai.md](https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/shanghai.md)

Short list

| EIPs | T-shirt size | Status | PR  | Champion | Understudy | Accepted? | Needed for Devnet? |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [3540](https://eips.ethereum.org/EIPS/eip-3540) - EVM Object Format (EOF) | XL  | in main | [https://github.com/hyperledger/besu/pull/4644](https://github.com/hyperledger/besu/pull/4644)  <br>  <br>Under discussion: [https://notes.ethereum.org/@ipsilon/eof1-unified-specification](https://notes.ethereum.org/@ipsilon/eof1-unified-specification) | Danno |     | Likely (EOF) | N   |
| [3651](https://eips.ethereum.org/EIPS/eip-3651) - Warm Coinbase | S   | in main | [https://github.com/hyperledger/besu/pull/4620](https://github.com/hyperledger/besu/pull/4620) | Danno |     | Yes | Y   |
| [3670](https://eips.ethereum.org/EIPS/eip-3670) - EOF - Code Validation | L   | in main | [https://github.com/hyperledger/besu/pull/4644](https://github.com/hyperledger/besu/pull/4644) | Danno |     | Likely (EOF) | y   |
| [3855](https://eips.ethereum.org/EIPS/eip-3855) - PUSH0 Instruction | S   | in main | [https://github.com/hyperledger/besu/pull/4660](https://github.com/hyperledger/besu/pull/4660) | Danno |     | Yes | Y   |
| [3860](https://eips.ethereum.org/EIPS/eip-3860) - Limit & Meter Initcode | M   | in main | [https://github.com/hyperledger/besu/pull/4726](https://github.com/hyperledger/besu/pull/4726) | Diego |     | Yes | Y   |
| [4200](https://eips.ethereum.org/EIPS/eip-4200) - Relative Jump Instructions | M   | Draft | [https://github.com/hyperledger/besu/pull/4760](https://github.com/hyperledger/besu/pull/4760) | Diego |     | Likely (EOF) | Y   |
| [4750](https://eips.ethereum.org/EIPS/eip-4750) - EOF Functions | XL  | Draft | [https://github.com/hyperledger/besu/pull/4781](https://github.com/hyperledger/besu/pull/4781) | Danno |     | Likely (EOF) | y   |
| [4844](https://eips.ethereum.org/EIPS/eip-4844) - Shard Blob Tx | XL  |     | [https://github.com/hyperledger/besu/issues/4631](https://github.com/hyperledger/besu/issues/4631) | Jiri |     | Likely (Blobs) | Likely |
| [4895](https://eips.ethereum.org/EIPS/eip-4895) - Withdrawals | M   |     | [https://github.com/hyperledger/besu/issues/4746](https://github.com/hyperledger/besu/issues/4746) | Simon |     | Yes | Y   |
| [5450](https://eips.ethereum.org/EIPS/eip-5450) - EOF Stack Validation | M   |     |     | Danno |     | Likely (EOF) | y   |

Laundry list

| EIPs | T-shirt size | Status | PR  | Champion | Accepted? |
| --- | --- | --- | --- | --- | --- |
| [1153](https://eips.ethereum.org/EIPS/eip-1153) - Transient Storage | M   | testing | [#4118](https://github.com/hyperledger/besu/pull/4118) |     | Likely |
| [2537](https://eips.ethereum.org/EIPS/eip-2537) - BLS Precompile | S   | complete | in main | Gary | Likely |
| [3074](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiapbLbgP76AhXQF1kFHQ7nDLYQFnoECA0QAQ&url=https%3A%2F%2Feips.ethereum.org%2FEIPS%2Feip-3074&usg=AOvVaw1o2Be8KA6Z3aBwGKJ1lSnh) - AUTH and AUTHCALL | L   |     |     |     | Unlikely |
| [EIP-4758: Deactivate SELFDESTRUCT](https://eips.ethereum.org/EIPS/eip-4758)  <br>  <br>(note there's also now an alternative EIP  <br>[https://eips.ethereum.org/EIPS/eip-6046](https://eips.ethereum.org/EIPS/eip-6046)) | S   |     |     |     | Likely |