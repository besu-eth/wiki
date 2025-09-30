# 2022-06-21 Contributor Call - APAC Friendly Time

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
  - 22.4.3 complete [https://github.com/hyperledger/besu/releases/tag/22.4.3](https://github.com/hyperledger/besu/releases/tag/22.4.3)
  - Next planned release is 22.7.0-RC1 scheduled for 29 June (Danno) [Release Rotations 2022](../../../../besu/developing-and-conventions/releasing/archive/release-rotations-2022.md)
    - Should we release off main branch - discussion to happen on discord
- **Work Updates**
  - Code Audit starting 24 June
    - Primary focus is the engine APIs for Eth Merge
    - Nothing for you to do unless directly asked
  - Java 17 Migration
    - Status: Yellow
      - Possibly move to 22.10.0 release
    - All issues are mostly Build/CircleCI/testing related, not code related.
      - LGTM only supports up to Java 14 - [https://lgtm.com/help/lgtm/java-extraction](https://lgtm.com/help/lgtm/java-extraction)
        - CodeQL looks to be a successor project
      - CodeQL is having module issues (probably fixable)
      - latest JDK docker image is not Java 18, and upgrading to Java 18 requires new LTS of ubunutu, which is not signed yet
        - We could drop the "latest" variant.  It doesn't auto update and it is out of date.
      - testWindows is using he wrong JDK
      - TLSContextFactoryTest doesn't have the proper TLS libraries
        - Same with AcceptanceTests and org.hyperledger.besu.tests.acceptance.bft.pki.PkiQbftAcceptanceTest
- **Other Business**
  - Maintainers to update mainnet activity. Details to be shared on discord.
- **Metrics Review -** [Linux Foundation Project Besu Insights](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Open Forum**
  - GitHub issue discussion started from [Nicolas Massart](https://lf-hyperledger.atlassian.net/wiki/people/70121:5502de36-6082-4606-81f5-4fd4f51016ab?ref=confluence)
    - [writing a quick proposal](../2022-agendas/2022-06-07-contributor-call/make-besu-questions-easy-to-find-and-answer.md)
    - Post reminder on discord
- **Future Topics**
  - /Add item/ 

   

|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155669/GMT20220621-010324_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155669&fileName=GMT20220621-010324_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155669&fileName=GMT20220621-010324_Recording.txt) | Text File [GMT20220621-010324\_Recording.txt](/wiki/download/attachments/22155669/GMT20220621-010324_Recording.txt?api=v2) | Jul 14, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155669/GMT20220621-010324_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155669&fileName=GMT20220621-010324_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155669&fileName=GMT20220621-010324_Recording.transcript.vtt) | File [GMT20220621-010324\_Recording.transcript.vtt](/wiki/download/attachments/22155669/GMT20220621-010324_Recording.transcript.vtt?api=v2) | Jul 14, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155669/GMT20220621-010003_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155669&fileName=GMT20220621-010003_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155669&fileName=GMT20220621-010003_Recording.transcript.vtt) | File [GMT20220621-010003\_Recording.transcript.vtt](/wiki/download/attachments/22155669/GMT20220621-010003_Recording.transcript.vtt?api=v2) | Jul 14, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155669)