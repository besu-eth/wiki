# 2022-05-10 Contributor Call

(Meeting Link: ⁨[https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09](https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09))

EMEA Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 8 am Monday Los Angeles
- 11 am Monday New York

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - Incentive Program Update: [\[WIP\] Proposal #4](../../../../besu/programs-grants/besu-execution-client-incentive-program/wip-proposal-4.md) is considered the final proposal. EF, HLF, and CSI are currently working with their respective legal teams. The validators are up and running for now.  Here is the final documentation from the Hyperledger side:  [main.pdf](./attachments/main.pdf)
    - Thanks to Sally and Danno for their suggestions!  
    - Ask: start for community lead initiative for nominations
      - timeline: 6 months after the Merge
      - discussion on wiki or GitHub for the contributions: both for now
        - no design for duplication for now 
- **Release updates**
  - Tracking who is doing each release [Release Rotations 2022](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Release+Rotations+2022)
    - *22.4.0-RC2 complete.* 
    - *22.4.0 complete*
    - *22.4.1 scheduled for May 18th - Jason Frame (Australia) is down to execute this one* 
  - *discussion on merge and version sync*

**Work Updates**

- 
  - Merge Update:
    - *Ongoing UX and other bugs being raised and fixed quickly. Testnet was launched last week. Besu had some syncing challenges.* 
    - *Mainnet shadow fork on this Th*
  - *Snap Sync: Goerli and Mainnet sync has been tested. Adding benchmarks to identify any other issues. Next call: [Karim Taam](https://lf-hyperledger.atlassian.net/wiki/people/712020:595ffa36-5d5e-40b6-b7f0-b39c13201928?ref=confluence)to share broader update. Don't want to have usable snapsync on main branch yet. If it is ready to be tested, will share in besu-contributors once ready.* 
    - *working on a blog on results*
- **Other Business** 
  - Automated Security Bot Requests  
LinuxFoundation as a part of the insights process is creating an automated "security bot" that will analyze LF (and hence Hyperledger project).  The feature set is very low at the moment, but they are actively soliciting feature requests.  What would Besu want to see?
    - *No high priority requests.*
  - Debug Issue with Besu: (brought up by [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence): Having some challenges with Docker. Need to do more research to understand options/issue further. (no need to add in the next agendas)
  - Separate lists for code maintainers and non-code maintainers [https://github.com/hyperledger/besu/pull/3790](https://github.com/hyperledger/besu/pull/3790)
    - Should the approval process be different? Non-code maintainers can change status of tickets but can't approve PRs
    - PR to add 2 new non-code maintainers [https://github.com/hyperledger/besu/pull/3811](https://github.com/hyperledger/besu/pull/3811)
    - discussion if triage is working or not and looks like it is working: permissions are working for Execution Client triage
  - Security Audit Update? Timeline?
  - Validator Experience with Besu
    - [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence)  connecting with [David Boswell](https://lf-hyperledger.atlassian.net/wiki/people/70121:0a14f738-3039-421f-a6a9-a83d19f23227?ref=confluence)
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Roadmap Review - [Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)**
  - Note from Matt on 22.7 
  - optimistic support, rollup client diversity question 
    - [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence)  will engage more with those devs re changes rollups product requirement 
      - example on providing more APIs
- **Open Forum**  
  - Proposal - "Off Week" Discord voice chat meetup. When?
  - Deprecating log42j - from Diego see Contributor channel
- **Future Topics**

  

    **|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155574/main.pdf?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155574&fileName=main.pdf&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155574&fileName=main.pdf) | PDF File [main.pdf](/wiki/download/attachments/22155574/main.pdf?api=v2) | May 10, 2022 by [Hart Montgomery](/wiki/people/712020:86f447c0-86dc-43b3-ac03-6a31923bbb84) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155574/GMT20220510-145809_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155574&fileName=GMT20220510-145809_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155574&fileName=GMT20220510-145809_Recording.transcript.vtt) | File [GMT20220510-145809\_Recording.transcript.vtt](/wiki/download/attachments/22155574/GMT20220510-145809_Recording.transcript.vtt?api=v2) | May 19, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155574/GMT20220510-145809_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155574&fileName=GMT20220510-145809_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155574&fileName=GMT20220510-145809_Recording.txt) | Text File [GMT20220510-145809\_Recording.txt](/wiki/download/attachments/22155574/GMT20220510-145809_Recording.txt?api=v2) | May 19, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155574)**