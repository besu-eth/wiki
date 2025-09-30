# 2022-07-19 Contributor Call - APAC Friendly Time

(Meeting Link: ⁨[https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09](https://zoom.us/j/91405289771?pwd=QzA3a0ozTjVSZ0hsYzgwTm9lVDRPQT09))

APAC Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20220621T010000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20220621T010000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 6 pm Monday Los Angeles
- 9 pm Monday New York
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
  - /Add item/ 
- **Roadmap Review -** [Besu Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)
- **Release updates**
  - 22.7.0-RC1 done
  - 22.7.0-RC2 20 July - Danno
- **Work Updates**
  - Peering improvements - ongoing. Some current hypotheses being investigated:
    - Changing the way we detect and eliminate duplicate connections [https://github.com/hyperledger/besu/pull/4001](https://github.com/hyperledger/besu/pull/4001)
    - Changing the default max message size [https://github.com/hyperledger/besu/pull/4120](https://github.com/hyperledger/besu/pull/4120)
    - Checking if a peer is disconnected by the time we add them [https://github.com/hyperledger/besu/pull/4100](https://github.com/hyperledger/besu/pull/4100)
  - Adding discv5 support - starting investigation this week
    - [https://github.com/hyperledger/besu/issues/4087](https://github.com/hyperledger/besu/issues/4087)
    - there is a spec
    - discv5.1
    - using the consensys/discovery library which would be v5.1 and which is used already by Teku [https://github.com/ConsenSys/discovery/pull/72](https://github.com/ConsenSys/discovery/pull/72)
  - Eth\_call performance improvements - starting investigation next week
    - [https://github.com/hyperledger/besu/issues/3926](https://github.com/hyperledger/besu/issues/3926)
  - GraphQL spec updates - Danno - some EIPs that would be good to add - PR up for review [https://github.com/hyperledger/besu/pull/4112](https://github.com/hyperledger/besu/pull/4112)
    - more changes after this to add some quality of life improvements
- **Other Business**  
  - Add GitPOAP badge to README (added by Daniel): PR [#4107](https://github.com/hyperledger/besu/pull/4107)  
Notes by Daniel: I will not be on the call, but maybe a decision could be made if this PR should be merged or not. I don't have a strong opinion either way. 
    - no objections
    - add to besu-docs and besu-native also?
    - will it encourage contributions?
    - encouraging contributions to docs specifically would be useful - and is one of the hardest things to get ppl to contribute to
- **Metrics Review -** [Linux Foundation Project Besu Insights](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Open Forum**
  - /Add item/ 
- **Future Topics**
  - /Add item/ 

  

   

|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155735/GMT20220719-010420_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155735&fileName=GMT20220719-010420_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155735&fileName=GMT20220719-010420_Recording.transcript.vtt) | File [GMT20220719-010420\_Recording.transcript.vtt](/wiki/download/attachments/22155735/GMT20220719-010420_Recording.transcript.vtt?api=v2) | Jul 20, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155735/GMT20220719-010420_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155735&fileName=GMT20220719-010420_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155735&fileName=GMT20220719-010420_Recording.txt) | Text File [GMT20220719-010420\_Recording.txt](/wiki/download/attachments/22155735/GMT20220719-010420_Recording.txt?api=v2) | Jul 20, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155735)