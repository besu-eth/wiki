# 2022-04-26 Contributor Call

(Meeting Link: ⁨[https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09](https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09))

APAC Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 5 pm Monday Los Angeles
- 8 pm Monday New York
- 1 am  Tuesday UTC
- 3 am Tuesday Paris/Berlin
- 11 am Tuesday Brisbane

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - Incentive Program Update: [\[WIP\] Proposal #4](../../../../besu/programs-grants/besu-execution-client-incentive-program/wip-proposal-4.md) is considered the final proposal. EF, HLF, and CSI are currently working with their respective legal teams. 
    - update from [Hart Montgomery](https://lf-hyperledger.atlassian.net/wiki/people/712020:86f447c0-86dc-43b3-ac03-6a31923bbb84?ref=confluence) - ongoing meetings with legal teams. Broad agreement but need more specific details. Hart writing up a more detailed version of Tim's proposal.
      - Here is the draft pdf: [main.pdf](./attachments/main.pdf)
      - Here is the github with the raw text: [https://github.com/hartm/Besu-CIP-Proposal](https://github.com/hartm/Besu-CIP-Proposal).  Feel free to issue a PR if you like!
- **Roadmap Review - [Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)** 
  - Roadmap needs updating
- **Release updates**
  - 22.1.3 done [Stefan Pingel](https://lf-hyperledger.atlassian.net/wiki/people/5cad317cbb353819f2b62236?ref=confluence) [22.1.3](https://github.com/hyperledger/besu/releases/tag/22.1.3)
  - 22.4.0-RC1 done [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence) [22.4.0-RC1](https://github.com/hyperledger/besu/releases/tag/22.4.0-RC1) 
  - *RC 2 is scheduled for next week. [Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence) is on point to manage it.* 
    - *consensus bug (already merged)*
    - *IPC RPC feature (needs merge)*
  - *22.4.0 scheduled for 30 April. [Lucas Saldanha](https://lf-hyperledger.atlassian.net/wiki/people/557058:0d633bf4-2ffe-43aa-9885-fc8f4eb766fd?ref=confluence)on point to manage this one* 
    - *everything is on track. wait a week after RC2*
  - Tracking who is doing each release [Release Rotations 2022](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Release+Rotations+2022)
    - Add your name here to volunteer for release rotation
- **Work Updates**
  - Future Backwards Incompatible Changes ([Danno Ferrin](https://lf-hyperledger.atlassian.net/wiki/people/5b7f2d80c4e4892a5b789551?ref=confluence))
    - Java 17 migration (notice in next quarterly (22.4.0), actual upgrade next after (22.7.0))
      - consider changing JVMs for the docker images - temurin? (was adoptopenjdk) - popular in community
    - EVM migration from Gas object to long ([git branch](https://github.com/shemnon/besu/tree/longForGas)) (next quarterly ie 22.4.0)
- **Other Business** 
  - Automated Security Bot Requests  
LinuxFoundation as a part of the insights process is creating an automated "security bot" that will analyze LF (and hence Hyperledger project).  Feature set is very low at the moment, but they are actively soliciting feature requests.  What would Besu want to see?
    - can we view what is currently being scanned for? Current insights?
    - no action
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Open Forum**
  - Proposal - "Off Week" Discord voice chat meetup. Volunteers?
  - Deprecating log42j - from Diego see Contributor channel 
    - check if this has been resolved - log4j.xml
  - LGTM - fixed
  - Global forum program committee - 5-6 hrs reviewing sessions, 2 hrs meetings to discuss
  - Some discussion on submitting talks [https://events.linuxfoundation.org/hyperledger-global-forum/](https://events.linuxfoundation.org/hyperledger-global-forum/)
- **Future Topics**

    **|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155543/main.pdf?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155543&fileName=main.pdf&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155543&fileName=main.pdf) | PDF File [main.pdf](/wiki/download/attachments/22155543/main.pdf?api=v2) | Apr 25, 2022 by [Hart Montgomery](/wiki/people/712020:86f447c0-86dc-43b3-ac03-6a31923bbb84) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155543/GMT20220426-005935_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155543&fileName=GMT20220426-005935_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155543&fileName=GMT20220426-005935_Recording.transcript.vtt) | File [GMT20220426-005935\_Recording.transcript.vtt](/wiki/download/attachments/22155543/GMT20220426-005935_Recording.transcript.vtt?api=v2) | Apr 26, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155543/GMT20220426-005935_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155543&fileName=GMT20220426-005935_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155543&fileName=GMT20220426-005935_Recording.txt) | Text File [GMT20220426-005935\_Recording.txt](/wiki/download/attachments/22155543/GMT20220426-005935_Recording.txt?api=v2) | Apr 26, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155543)**