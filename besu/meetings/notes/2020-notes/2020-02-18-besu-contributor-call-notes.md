# 2020-02-18 Besu Contributor Call Notes

Recording of call - [https://consensys.zoom.us/rec/share/-MoqPu2uq31LYLfjzkbTU695IsfaT6a8hiIX8\_EKzkZI5\_dD51ilQUFRK4dlFt9h?startTime=1581987869000](https://consensys.zoom.us/rec/share/-MoqPu2uq31LYLfjzkbTU695IsfaT6a8hiIX8_EKzkZI5_dD51ilQUFRK4dlFt9h?startTime=1581987869000)

Housekeeping

General Announcements

- Conferences
  - [ETHDenver](https://www.ethdenver.com/)  
    - Successful conference
    - DApp focused and so no Besu bounty was taken
    - Working towards stateless Ethereum
  - [ETHCC](https://ethcc.io/) is still coming
  - [Hyperledger Global Forum](https://www.hyperledger.org/event/hyperledger-global-forum-2020)
    - We are still on given the travel restrictions, but watch this space

Release Updates

- 1.3.9  
  - ETC release for fork support
- 1.4RC
  - Going to have an RC2 this week, with full release planned for next week
  - Everything planned should be in

Work updates

- The ETC migration from ethash to keccak256 is to level the ASIC playing field, rather than trying to keep being ASIC resistant
- The roadmap page will be updated shortly with the plans for 1.5
  - Performance improvements
  - Improvements to the private state support
  - Beam sync, especially important as a first step to being a stateless client
  - Mining support improvements
    - Transaction pool management

Other Business

- N/A

Open Forum

- Fast vs Full sync from [Aditya Singh](https://lf-hyperledger.atlassian.net/wiki/people/557058:98f1b638-6c48-4c47-9801-ef016b4d7ee5?ref=confluence)  
  - Security guarantees are about the same if you validate the pivot block
  - Ethereum is different to Bitcoin in that each block includes the root hash from a petricia tree of the unspent transactions which allows us to start in the middle