# 2024-01-30 Contributor Call - APAC Friendly Time

(Meeting Link: ⁨[https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09](https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09))

APAC Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20220621T010000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20220621T010000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 5 pm Monday Los Angeles
- 8 pm Monday New York
- 1 am  Tuesday UTC
- 3 am Tuesday Paris/Berlin
- 11 am Tuesday Brisbane

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless you are speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - Dencun on Sepolia on the 30th [2024-01-30 22:51:12](https://www.timeanddate.com/worldclock/converter.html?iso=20240130T225100&p1=1440&p2=37&p3=136&p4=237&p5=923&p6=204&p7=671&p8=16&p9=41&p10=107&p11=28) UTC. Need to update Besu to at least 24.1.0 and your CL to latest version
    - Add a reminder on our discord to check your EL and CL are updated
  - Dencun on Holesky 7th February [2024-02-07 11:34:24](https://www.timeanddate.com/worldclock/converter.html?iso=20240207T113400&p1=1440&p2=37&p3=136&p4=237&p5=923&p6=204&p7=671&p8=16&p9=41&p10=107&p11=28) UTC
  - See EF announcement here [https://blog.ethereum.org/2024/01/24/sepolia-holesky-dencun](https://blog.ethereum.org/2024/01/24/sepolia-holesky-dencun)
- **Roadmap Review** 
- **Release updates**
  - 24.1.1 release
    - Release artifacts are safe, and SHAs have been updated. It was a CI issue.
- **Work Updates**
  - GitHub actions CI
    - PR is [https://github.com/hyperledger/besu/pull/6427](https://github.com/hyperledger/besu/pull/6427)
      - Looking like we will move to GHA tomorrow
      - Some followup work
        - Making builds repeatable builds
    - Still targeting 24.1.2
  - Besu opinions on Prague [The Prague Upgrade from Besu Maintainers - The Hot, Cold, & Open-Ended](../../../../besu/besu-roadmap-planning/prague-planning/the-prague-upgrade-from-besu-maintainers-the-hot-cold-open-ended.md)
  - Experimental storage improvements with Trielog limiting 
    - stands to save > 3GB per week. (~160GB per year)
    - [Limit Trie Logs](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Limit+Trie+Logs) 
    - [https://github.com/hyperledger/besu/issues/5390](https://github.com/hyperledger/besu/issues/5390)
  - Snap sync to finally become *officially* production-ready (has been our recommended default for some time) [https://github.com/hyperledger/besu/pull/6405](https://github.com/hyperledger/besu/pull/6405)
    - The first change is to rename X\_SNAP → SNAP and X\_CHECKPOINT → CHECKPOINT
    - Follow on work to create profiles for changing default [Change to Besu Defaults - Q1 2024](../../../../besu/design-documents/change-to-besu-defaults-q1-2024.md)
- **Other Business**
  - /add item/
- **Open Forum**
  - /add item/
- **Future Topics**
  - /add item/

  

**Recordings**

Find the recording in the playlist - **[https://www.youtube.com/playlist?list=PL0MZ85B\_96CHpqsKmljUK8HB98wK67RjC](https://www.youtube.com/playlist?list=PL0MZ85B_96CHpqsKmljUK8HB98wK67RjC)**

   

|     | File | Modified |
| --- | --- | --- |

No files shared here yet.

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description