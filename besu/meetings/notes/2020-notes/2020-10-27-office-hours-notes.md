# 2020-10-27 Office Hours Notes

Agenda

- General Announcements
  - added notes about hyperledger developer newsletter 
  - Future of Ethereum Summit last Friday - [lots of recorded talks](https://ethonline.org/future/)
- Release Process
  - 20.10.0-RC 2 last week - 21 October
  - 20.10.0 FCS next week 3/4 November
- Work Updates
- Other Business  
  - No Pending Proposals

## Ethereum Hard Forks.  Who, What, When, Where, How, Why

Berlin EIPs

Current Berlin EIPs

[https://github.com/ethereum/eth1.0-specs/blob/master/client-integration-testnets/YOLOv2.md](https://github.com/ethereum/eth1.0-specs/blob/master/client-integration-testnets/YOLOv2.md)

- EVM Subroutines (EIP-2315)
- BLS12 precompile contracts (EIP-2537)
- Access List Account Access (EIP-2929)

to run Yolo v2 with 

\`docker run hyperledger/besu:develop --Xberlin-enabled=true --network=yolo\_v2 --sync-mode=full\`

Possible Berlin EIPs

EIP-2146 - Precpompile static call cost (mooted by EIP-2929)  
EIP-2565 - ModEXP Repricing  
EIP-2718 - Transaction enveloping  
EIP-2930 - access list in TX envelope  
  

What does a consensus bug look like?

- we get a block rejected log line
- 3 apis to help us look: \`debug\_getBadBlocks\`, \`debug\_standardTraceBlockToFile\`, \`debug\_standardTraceBadBlockToFile\`
- EF has nodes set up to try and detect bad blocks and automate information gathering for the client teams.