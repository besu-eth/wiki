# 2022-11-11 Fork on Sepolia

# TL;DR:

critical bug in RC3 strawman causing fork on sepolia

fix is in main [Remove Bytes32.ZERO](https://github.com/hyperledger/besu/pull/4578)

and in RC3 [merge 4578 removing Bytes32.ZERO](https://github.com/hyperledger/besu/pull/4579)

will make public once fix is verified and we know it’s not exploitable on mainnet

Updated RC3 has been deployed to:

- sepolia and ropsten validator nodes
- new node dev-besu-clc-teku-ohio-goerli-dev-22.10.0-goerli-burn-in2 and
- new node dev-besu-clc-teku-ohio-mainnet-dev-22.10.0-mainnet-burn-in4

# Summary

All of our besu sepolia canaries (running 22.10.0-RC3-SNAPSHOT aka strawman [https://github.com/hyperledger/besu/commit/8204f9a1051152639986f289711cc20dd94b9514](https://github.com/hyperledger/besu/commit/8204f9a1051152639986f289711cc20dd94b9514) ) were displaying “blocks behind” alerts

# Invalid transaction

stack trace - Note IllegalArgumentException: An account address must be 20 bytes long, got 32.

```
{"@timestamp":"2022-10-31T00:42:16,431","level":"INFO","thread":"vert.x-worker-thread-0","class":"AbstractBlockProcessor","message":"Block processing error: transaction invalid Internal Error in Besu - java.lang.IllegalArgumentException: An account address must be 20 bytes long, got 32. Block 0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad Transaction 0xea993da47eb3cc4a7d549cd5b2d52bae5b0770807f36e10aad72480d75cdd026","throwable":""}
{"@timestamp":"2022-10-31T00:42:16,432","level":"INFO","thread":"vert.x-worker-thread-0","class":"MainnetBlockValidator","message":"Optional[Block processing error: transaction invalid Internal Error in Besu - java.lang.IllegalArgumentException: An account address must be 20 bytes long, got 32. Block 0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad Transaction 0xea993da47eb3cc4a7d549cd5b2d52bae5b0770807f36e10aad72480d75cdd026]. Block 2192803 (0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad)","throwable":""}
{"@timestamp":"2022-10-31T00:42:16,432","level":"WARN","thread":"vert.x-worker-thread-0","class":"EngineNewPayload","message":"Invalid new payload: number: 2192803, hash: 0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad, parentHash: 0x7385267518859cf18f7844eb4143dfc1754f724cb158e9b8ac87932cec26b526, latestValidHash: 0x7385267518859cf18f7844eb4143dfc1754f724cb158e9b8ac87932cec26b526, status: INVALID, validationError: Block processing error: transaction invalid Internal Error in Besu - java.lang.IllegalArgumentException: An account address must be 20 bytes long, got 32. Block 0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad Transaction 0xea993da47eb3cc4a7d549cd5b2d52bae5b0770807f36e10aad72480d75cdd026","throwable":""}
```

- TODO fill out this ticket with details [https://github.com/hyperledger/besu/issues/4577](https://github.com/hyperledger/besu/issues/4577)

Side effect of the Address → Bytes32 change from Danno [https://github.com/hyperledger/besu/pull/4562](https://github.com/hyperledger/besu/pull/4562)

Theory - from Danno

What I think happened is an unused storage slog got an SLOAD, which loaded as a Byte32.ZERO, which is a ConstantBytes32Value. This was attempted to be converted to an address, that requires 20 bytes. the slice method on ConstantBytes32Value is buggy and returns a 32 byte value always.

There’s a **bug in Tuweni** whereby slice of Bytes32.ZERO ALWAYS gives 32 bytes regardless of slice params

- [https://github.com/apache/incubator-tuweni/issues/445](https://github.com/apache/incubator-tuweni/issues/445)

## FIX

So the fix was to totally eliminate Bytes32.ZERO from Besu codebase

- PR from Danno [Remove Bytes32.ZERO](https://github.com/hyperledger/besu/pull/4578)

Gathering additional evidence to support Danno’s theory - trace for bad block

curl --location --request POST '[http://localhost:8545/](http://localhost:8545/)' \\ --data-raw '{ "jsonrpc": "2.0", "method": "debug\_standardTraceBadBlockToFile", "params": \[ "0x2d4042856d73d6c82fcd7a3f1088418ed0e5eed68d1ed6c78d68d5ca89b440ad" \], "id": 1 }'

zip of resulting files:

From Danno -

> 95% certain. FRom TX 0
> 
> {"pc":621,"op":84,"gas":"0x905","gasCost":"0x834","memory":"0x000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080","memSize":96,"stack":\["0xb07943a","0x6b","0x12d","0x128","0x360894a13ba1a3210667c828492db98dca3e2076cc3735a920a3ca505d382bbc"\],"returnData":null,"depth":2,"refund":0,"opName":"SLOAD","error":""} {"pc":622,"op":144,"gas":"0x902","gasCost":"0x3","memory":"0x000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080","memSize":96,"stack":\["0xb07943a","0x6b","0x12d","0x128","0x0"\],"returnData":null,"depth":2,"refund":0,"opName":"SWAP1","error":""}
> 
> SLOAD pushed zero on the stack. The exception at the end of trace prevents the DELEGATECALL from being added to the trace, where the 0x0 address (which is Bytes32.ZERO) is converted to an address and the errooneous split method is invoked.

## Verify

I updated release-22.10.x branch [https://github.com/hyperledger/besu/tree/release-22.10.x](https://github.com/hyperledger/besu/tree/release-22.10.x)

- with a cherry-pick [https://github.com/hyperledger/besu/pull/4579](https://github.com/hyperledger/besu/pull/4579)

manually downloaded the tar file and updated one canary node (besu-lighthouse-sepolia) and it seems happy now. 0 blocks behind, 0 bad blocks as per debug\_getBadBlocks

using the CLC sepolia jenkins job to update all the sepolia nodes

- restarted nimbus
- restarted lodestar
- all seem to be recovering

Interesting that the teku one is taking the longest to recover

All caught up (graph)