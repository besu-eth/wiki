# 2022-06-07 Contributor Call

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
- **General Announcements**
  - mentioning [this](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Mainnet+activity+log+H1+2023) from Hart
- **Release updates**
  - Tracking who is doing each release [Release Rotations 2022](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Release+Rotations+2022)
    - 22.4.3 - June 14th - Justin
  - *discussion on merge and version sync*

**Work Updates**

- 
  - Merge Update (Justin):
    - *Ongoing UX and other bugs being raised and fixed quickly.* 
    - How best to disconnect from PoW network. 
      - Empty proposals after TTD - [https://github.com/hyperledger/besu/issues/3890](https://github.com/hyperledger/besu/issues/3890)
        - Why do we drop incoming TX while not in sync with best peer? [https://github.com/hyperledger/besu/pull/3937](https://github.com/hyperledger/besu/pull/3937)
        - Is it safe to drop peers that are still on the PoW network? This would require re-querying their total difficulty.
  - *Checkpoint sync merged on main*
    - *(genesis block, Karim)*
    - *background mechanism (similar to GETH)*
    - *checkpoints update*
      - *last one November*
    - *once ready.* 
      - *working on a blog on results* 
    - ***reminder: putting that to the release checklist from Gary***
- **Other Business** 
  - Automated Security Bot Requests  
LinuxFoundation as a part of the insights process is creating an automated "security bot" that will analyze LF (and hence Hyperledger project).  The feature set is very low at the moment, but they are actively soliciting feature requests.  What would Besu want to see?
    - *No high priority requests.*
  - Separate lists for code maintainers and non-code maintainers [https://github.com/hyperledger/besu/pull/3790](https://github.com/hyperledger/besu/pull/3790)
    - Should the approval process be different? Non-code maintainers can change status of tickets but can't approve PRs
    - PR to add 2 new non-code maintainers [https://github.com/hyperledger/besu/pull/3811](https://github.com/hyperledger/besu/pull/3811)
    - discussion if triage is working or not and looks like it is working: permissions are working for Execution Client triage
  - Security Audit Update? Timeline?
    - discord discussion
  - Validator Experience with Besu
    - [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence)  connecting with [David Boswell](https://lf-hyperledger.atlassian.net/wiki/people/70121:0a14f738-3039-421f-a6a9-a83d19f23227?ref=confluence)
    - framework to engage with merge audience to tailor workshop
      - before merge
      - later merge
      - no ETA yet 
      - [Francesco Andreoli](https://lf-hyperledger.atlassian.net/wiki/people/610104864e8d8d0069291688?ref=confluence)helping organizing
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Roadmap Review - [Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)**
  - Note from Matt on 22.7 
    - fixing, testing with EF 
  - optimistic support, rollup client diversity question 
    - [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence)  will engage more with those devs regarding changes rollups product requirement 
      - example on providing more APIs
  - New addition - peering improvement and node operations improvement
    - improving node operations (Helen input)
    - scale faster, investigations on lowering cost
    - version release discussion 
      - quarterly releases
- **Open Forum**  
  - chitchat calendar in the calendar - besu group - (Todo [Francesco Andreoli](https://lf-hyperledger.atlassian.net/wiki/people/610104864e8d8d0069291688?ref=confluence) )
    - it’ll be this time/day next week, and then alternating with this meeting
  - GitHub issue discussion started from [Nicolas Massart](https://lf-hyperledger.atlassian.net/wiki/people/70121:5502de36-6082-4606-81f5-4fd4f51016ab?ref=confluence)
    - [writing a quick proposal](./2022-06-07-contributor-call/make-besu-questions-easy-to-find-and-answer.md)
- **Future Topics**

  

    **|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155603/main.pdf?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155603&fileName=main.pdf&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155603&fileName=main.pdf) | PDF File [main.pdf](/wiki/download/attachments/22155603/main.pdf?api=v2) | May 10, 2022 by [Francesco Andreoli](/wiki/people/610104864e8d8d0069291688) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155603/GMT20220607-145708_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155603&fileName=GMT20220607-145708_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155603&fileName=GMT20220607-145708_Recording.transcript.vtt) | File [GMT20220607-145708\_Recording.transcript.vtt](/wiki/download/attachments/22155603/GMT20220607-145708_Recording.transcript.vtt?api=v2) | Jun 07, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155603/GMT20220607-150205_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155603&fileName=GMT20220607-150205_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155603&fileName=GMT20220607-150205_Recording.transcript.vtt) | File [GMT20220607-150205\_Recording.transcript.vtt](/wiki/download/attachments/22155603/GMT20220607-150205_Recording.transcript.vtt?api=v2) | Jun 07, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155603/GMT20220607-150205_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155603&fileName=GMT20220607-150205_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155603&fileName=GMT20220607-150205_Recording.txt) | Text File [GMT20220607-150205\_Recording.txt](/wiki/download/attachments/22155603/GMT20220607-150205_Recording.txt?api=v2) | Jun 07, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155603)**