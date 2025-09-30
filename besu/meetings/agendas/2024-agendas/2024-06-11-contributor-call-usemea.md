# 2024-06-11 Contributor Call - US/EMEA

  

(Meeting Link: ⁨[https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09](https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09))

EMEA Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20220607T150000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20220607T150000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 8 am Tuesday Los Angeles time
- 11 am Tuesday New York time
- 17h Tuesday Paris time

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **Release updates / issues** 
  - 24.6.0 in burn-in phase for release 
  - Besu-Native (Gary and Matt Whitehead on action items) 
    - Some workarounds for current issues with release and local build.
    - How does this supply chain work so vendors and users can reliably build from specific commits against Besu-Native versions? 
      - Checks in the artifacts? Maven/JFrog/GHA? 
      - Need to review the code for verification of native in Besu-Main.
    - Besu-Native should now automatically derive a CalVer release from when it was built to avoid the overwrite problem of previous versions. 
      - Should target the same changes to release updates / GHA. 
      - Gradle properties file needs to be manually up-revved when a new version is being cut. 
      - Gary to take point on this. 
    - Maven should stop a version being released.
- **Work Updates**
  - Release updates in the Wiki from Justin - looking for feedback: [Release Process](../../../../besu/developing-and-conventions/releasing/release-process.md)
  - QBFT + Bonsai Updates
    - Two PRs raised alongside testing --
      - Enabling Snapsync / Bonsai for BFT - [https://github.com/hyperledger/besu/pull/7140](https://github.com/hyperledger/besu/pull/7140)
      - Fix for BFT state updates in Bonsai (invalid block issues) - [https://github.com/hyperledger/besu/pull/7204](https://github.com/hyperledger/besu/pull/7204)
    - Working through network and topology testing   
      - Some edge cases and implications for networks running new topologies (Snap / Bonsai)
    - Performance testing is next when Bonsai and QBFT can run in perpetuity without blocking bugs 
    - So far, so good
  - Legacy Features Sunset Plan – [https://docs.google.com/document/d/1MmFQde4C–JHvQWMabU7GyYwODYG3EhnT9IZ4uY8B4o/edit]
    - Blog post announcement forthcoming for maintainer feedback 
  - Maintainers -- LFR:
    - [https://github.com/hyperledger/besu/pull/6593](https://github.com/hyperledger/besu/pull/6593)
- **Other Business**
  - Review CI credit usage and build time for the month [https://app.circleci.com/insights/gh/hyperledger](https://app.circleci.com/insights/gh/hyperledger)
- **Open Forum**
  - /add item/
- **Future Topics**
  - /add item/

**Recordings**

Find the recording in the playlist - [https://www.youtube.com/playlist?list=PL0MZ85B\_96CHpqsKmljUK8HB98wK67RjC](https://www.youtube.com/playlist?list=PL0MZ85B_96CHpqsKmljUK8HB98wK67RjC)

   

|     | File | Modified |
| --- | --- | --- |

No files shared here yet.

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description