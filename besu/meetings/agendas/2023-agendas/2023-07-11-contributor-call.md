# 2023-07-11 Contributor Call

(Meeting Link: ⁨[https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09](https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09))

EMEA Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20230412T160000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20230412T160000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 9 am Tuesday Los Angeles time
- 12 am Tuesday New York time
- 18h Tuesday Paris time

**Agenda**

- **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - Q2 Report submitted - [https://github.com/hyperledger/toc/pull/133](https://github.com/hyperledger/toc/pull/133)
- **Release updates**
  - 23.4.4 - Bug fix release 
  - 23.7.0 - Upcoming (Burn-in Friday the 21st) 
    - New layered tx pool as the Mainnet default
      - Running on production validators
      - Bug fixes uncovered to be included in the 23.7.0 release
      - Old pool could still be enabled 
      - Private networks → Default of 200 future tx by account was bumped to 500 in testing and didn't impact performance 
      - Avoiding any limit for local transactions (needs to be implemented) - might help with private network use-case.
        - Another flag (default allow all?) that allows you to tune local transactions allowed in the pool
    - BONSAI as default (need discovery)
- **Work Updates**
  - Discussion of consensus mechanism plug-ins/modularity →
    - [Modular Consensus](../../../../besu/design-documents/modular-besu/modular-consensus.md) - Working group / Approach 
      - Start with PoW?
      - Setting meeting at the end of July for working group start → Matt N to share in #besu-contributors
      - Matt N to send materials on Plug-In system to call participants (Nischal, George, Diego, Matt W, Justin F)
    - Miro → [https://miro.com/app/board/uXjVMCPHPfg=/?share\_link\_id=795349574835](https://miro.com/app/board/uXjVMCPHPfg=/?share_link_id=795349574835) (Password: hyperledger)
    - [Modularity Review](../../../../besu/design-documents/modular-besu/modularity-implementation-approach.md)
  - Technical documentation requests → 
    - Plug-ins and new updates to the features → Matt N to create a page for plug-in system feedback and pain-points and details/tutorials/questions
      - Any time we update the plug-in API, we need to make sure we bring this back to the documentation
      - Need to make sure we are cataloging design goals and approaches
      - Specification of interface between the plug-ins and Besu as we modify the code in the docs
    - Trie-log shipping → Gary, Karim  
      - Need to place this back in the API docs
    - EVM Library 
    - More ![(question)](https://lf-hyperledger.atlassian.net/wiki/s/1449019483/6452/ae2804514f9cd9ed0d0281971dae9dc8f3187953/_/images/icons/emoticons/help_16.png)
  - Deprecation
    - ✅ Future removal of the Forest world state pruning [https://besu.hyperledger.org/en/stable/public-networks/reference/cli/options/#pruning-enabled](https://besu.hyperledger.org/en/stable/public-networks/reference/cli/options/#pruning-enabled)
    - ✅ Database version 0 - [https://github.com/hyperledger/besu/pull/5681](https://github.com/hyperledger/besu/pull/5681)
    - ✅ GoQuorum Compatible Privacy - [https://github.com/hyperledger/besu/pull/5607](https://github.com/hyperledger/besu/pull/5607)
  - Checker Framework 
    - [https://github.com/hyperledger/besu/pull/5536#discussion\_r1247180442](https://github.com/hyperledger/besu/pull/5536#discussion_r1247180442)
    - Opening a PR against Danno's EVM performance work to see the state of the EVM with these changes later on → Justin F
- **Other Business**
  - REPEAT: RFC - [Proposal: Avoid Cherry-Picked Releases](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Proposal%3A+Avoid+Cherry+Picked+Releases) - added *Suggested Deprecation Policy*
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Open Forum**
  - Performance Testing with Caliper - Web3Labs
    - IBFT/QBFT testing, performance is not that great
    - Ameziane & Nischal → to collaborate on Discord, Ameziane to provide advice on set-up and tests and review some results 
    - Block processing is done 3 times per block on QBFT networks → Ameziane POC [https://github.com/ahamlat/besu/tree/cache-validation-block](https://github.com/ahamlat/besu/tree/cache-validation-block)
- **Future Topics**

  

**Recording**

- **[https://youtu.be/cYYXEp9NW7I](https://youtu.be/cYYXEp9NW7I)**
- **[2023 07 11 Besu chat.txt](https://lf-hyperledger.atlassian.net/wiki/download/attachments/22156281/2023%2007%2011%20Besu%20chat.txt?version=1&modificationDate=1689100393000&cacheVersion=1&api=v2)**
- **[2023 07 11 Besu transcript.txt](https://lf-hyperledger.atlassian.net/wiki/download/attachments/22156281/2023%2007%2011%20Besu%20transcript.txt?version=1&modificationDate=1689100393000&cacheVersion=1&api=v2)**