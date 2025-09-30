# 2021-08-31 Besu Contributor Call

(Meeting Link: ⁨[https://consensys.zoom.us/j/95691099798](https://www.google.com/url?q=https://consensys.zoom.us/j/95691099798&sa=D&source=calendar&ust=1621094747216000&usg=AOvVaw0DzE1ZLz6VqnubaLGDkBoj))

EMEA/AMER Friendly Time -  1500 UTC ([https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 8 AM Tuesday San Francisco
- 11 AM Tuesday New York
- 3 PM Tuesday UTC
- 5 PM Tuesday Paris/Berlin
- 1 AM Wednesday Brisbane

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
- **Release updates**
  - Current release cadence 
    - Every two weeks, Tuesday (until something changes)
    - First beta cycle in September
    - Update protocol releases in the calendar [here](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Future+Release+Dates) ([Francesco Andreoli](https://lf-hyperledger.atlassian.net/wiki/people/610104864e8d8d0069291688?ref=confluence) [Matthew Wright (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/5fb2ceb04a09640069c6345f?ref=confluence) )
- **Work Updates** 
  - EVM Modularization
    - Prototype Separation complete - [https://github.com/shemnon/besu/tree/evmModule/evm](https://github.com/shemnon/besu/tree/evmModule/evm)
      - [https://github.com/shemnon/besu/pull/9](https://github.com/shemnon/besu/pull/9) shows the diffs
    - What should be the strategy to bring the changes in?  Align it with a quarterly release?  Piecemeal Changes?
    - Some Broad Changes
      - Move `Address` , `Hash`  and `Wei`  to a shared lib `datatypes` .
      - Move EVM classes to a new module
  - After cash implementation switch to Caffeine discussion (from Guava)
    - No licensing issue at least with Caffeine (It’s Apche2.0)
    - no problem having two implementations 
  - Base fee adjustment discussion
- **Other Business** 
  - Timeline for migration from RocketChat to Matrix → [https://chat.lfx.linuxfoundation.org/#/welcome](https://chat.lfx.linuxfoundation.org/#/welcome)
    - Francesco and Matt W to work on schedule posts to incentivize new chat engagement 
    - Start with Besu contributor channel and have them join other chat 
    - 1-2 month schedule 
  - Good first issues for Open Source Day
  - TSC Election Nominations have kicked off
- **Open Forum**
- **Future Topics**

  

**Recording:** 

[https://consensys.zoom.us/rec/share/-9whpiZ-FA2QoFL4PBmh7scaa6DDcXRUUlsyMAtqRxRHNFbcTUuWnLEp\_9rxIrKK.ZI2IsrXCwgZQGugG](https://consensys.zoom.us/rec/share/-9whpiZ-FA2QoFL4PBmh7scaa6DDcXRUUlsyMAtqRxRHNFbcTUuWnLEp_9rxIrKK.ZI2IsrXCwgZQGugG) 

**Passcode: R5J\*vE9x  
**