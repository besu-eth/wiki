# 2024-01-23 Contributor Call - AMEA Friendly Time

  

(Meeting Link: ⁨[https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09](https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09))

AMEA Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20230123T170000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20230123T170000&p1=224&p2=179&p3=1440&p4=195&p5=47))

San Francisco, USA     Mon, Jan 23, 2023 at 9:00 am PST  
New York, USA          Mon, Jan 23, 2023 at 12:00 noon EST  
UTC, Time Zone         Mon, Jan 23, 2023 at 5:00 pm   
Paris, France          Mon, Jan 23, 2023 at 6:00 pm CET  
Brisbane, Australia    Tue, Jan 24, 2023 at 3:00 am AEST

  

**Agenda**

-  **Migration from Circle CI to Github Actions.**
  - LAST CALL on feedback for GHA migration. Will propose using it (with CircleCI still available as a backup) for the 24.1.2 release.
  - PR is [https://github.com/hyperledger/besu/pull/6427](https://github.com/hyperledger/besu/pull/6427)
  - Design Doc is [https://lf-hyperledger.atlassian.net/wiki/pages/viewpage.action?pageId=22155998](https://lf-hyperledger.atlassian.net/wiki/pages/viewpage.action?pageId=22155998) 
  - NOTES:
    - Consensys team to test that maintainers can re-run jobs with current permissions
    - Consensys team to run CircleCI in parallel and measure results from GHA release (ensure that it works and disable Circle)
    - Acceptance on plan broad strokes, targeting 24.1.2 release with GHA (backup Circle)
    - Getting GHA merged in quickly so we can use snapshot builds
- **Defaults** 
  - Targeting 24.1.2 release 
  - Considering renaming selfish-staker profile
  - Need to determine mechanism for getting everyone to a fully flattened DB (with or without resync)
- **Performance** 
  - **[2024 - Besu Performance Improvements since the Merge](../../../../besu/performance-stability/2024-besu-performance-improvements-since-the-merge.md)**
- **Prague Planning**
  - Matt to create and outline a document for Besu team Prague scope opinions.
  - Consensys team to see if MM willing to discuss 3074
- **Roadmap**
  - QBFT-focused fuzzing? 
  - Acceptance tests run selectively for QBFT networks (price, filtered out of current gradle tasks, available on-demand)
    - Price analysis 
    - Specific follow up call scheduled 
  - Public/Private feature parity
    - Snap - need test cases for QBFT and Snap (snap server & snap client tests)
    - Soak / burn testing needs to consider private QBFT networks 
      - Sequenced pool needs to be exercised (can be done on Mainnet, private nets)
      - Long-lived, substantial state QBFT network ![(question)](https://lf-hyperledger.atlassian.net/wiki/s/1449019483/6452/ae2804514f9cd9ed0d0281971dae9dc8f3187953/_/images/icons/emoticons/help_16.png)
 
        - Repeatable!
    - Scheduled GHA for private nets? 

  

**Recordings**