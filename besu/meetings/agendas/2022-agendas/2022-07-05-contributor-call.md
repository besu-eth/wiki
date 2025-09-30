# 2022-07-05 Contributor Call

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
    - Tim Beiko (in charge of the Besu CIP program from the EF side) likes our format.  Please go ahead and document your mainnet contributions this year (starting from Jan. 1).  Thanks!
      - [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence)adding some points in the doc
    - There will (finally) be a meeting to put together a sub-HLF organization to handle the grant money on Wednesday.
    - (Hart:  I am double-booked and probably can't make the meeting.  Sorry!).
- **Release updates**
  - Tracking who is doing each release [Release Rotations 2022](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Release+Rotations+2022)
    - 22.4.3 - June 14th - Justin
      - Sepolia merge is tomorrow 6 July
    - 22.7.0-RC1 was delayed to develop the fix in [PR#4041](https://github.com/hyperledger/besu/pull/4041)
      - Danno is disconnected from the internet until Jul 8 and cannot run the release
      - Also, Java 17 support has been bumped to 22.10.0 because CI build tools don't support Java 17 to the level we need yet
  - *discussion on merge and version sync*
- ***RPC - Extra fields in transaction serialization (from [Daniel Lehrner](https://lf-hyperledger.atlassian.net/wiki/people/712020:65dd696b-014d-45f5-8ae1-776ca8026634?ref=confluence) )***
  - *When returning a transaction we return two fields that are not part of the spec: public key and raw. Should we keep them or not?  
*
  - *Discussion on Eth R&D Discord: [https://discord.com/channels/595666850260713488/910910348922589184/991299338133327894](https://discord.com/channels/595666850260713488/910910348922589184/991299338133327894)*
    - *Danno's thoughts in the Eth R&D Discord - [https://discord.com/channels/595666850260713488/910910348922589184/993556490487087155](https://discord.com/channels/595666850260713488/910910348922589184/993556490487087155)  
*
    - *Danno's thoughts in the HLF discord - [https://discord.com/channels/905194001349627914/992724025870651392/993557409542979695](https://discord.com/channels/905194001349627914/992724025870651392/993557409542979695)*
    - *[Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence) agree with what Karim suggested to get rid of those fields: you can still treat the client as a black-box. Need more discussion on spec architecture* 
  - *Own of this investigation RPC compatibility:* *[Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence)but no commitment on time/ pre-merge, not urgent*
- ***Liveness Check (issue [#4007](https://github.com/hyperledger/besu/issues/4007) form [Daniel Lehrner](https://lf-hyperledger.atlassian.net/wiki/people/712020:65dd696b-014d-45f5-8ae1-776ca8026634?ref=confluence) )***
  - *Our liveness check currently is just a stub. There was a user request to implement a proper check. Should we do that? If yes, what would we check?*
  - *Definition of liveness (and readiness) by RedHat: [https://cloud.redhat.com/blog/liveness-and-readiness-probes](https://cloud.redhat.com/blog/liveness-and-readiness-probes)*
  - *question: should we move the endpoints?*
  - *[Daniel Lehrner](https://lf-hyperledger.atlassian.net/wiki/people/712020:65dd696b-014d-45f5-8ae1-776ca8026634?ref=confluence) will update the doc and close with a documentation*

**Work Updates**

- 
  - Merge Update ([Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/60be12f85c64b100711c51d4?ref=confluence) )
    - blog post [here](https://hackmd.io/mt18qUMWRHiVZpFr9zwmlQ) also doing apost mortem of what happened etc
    - Mainnet shadow fork worked well
    - Sepolia happening tomorrow, 6 July
- **Other Business**
  - **[Nicolas Massart](https://lf-hyperledger.atlassian.net/wiki/people/70121:5502de36-6082-4606-81f5-4fd4f51016ab?ref=confluence)**  update on documentation  
    - using github discussions etc.
      - we don't have any consensus on this yet
      - we will not move forward with this at the moment
    - **sponsorware** sponsorship from HL referencing [this](https://squidfunk.github.io/mkdocs-material/insiders/)
      - action point: [Nicolas Massart](https://lf-hyperledger.atlassian.net/wiki/people/70121:5502de36-6082-4606-81f5-4fd4f51016ab?ref=confluence) will reach out per email to [community-architects@hyperledger.org](mailto:community-architects@hyperledger.org)
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Roadmap Review - [Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)**
  - optimistic support, rollup client diversity question 
  - New addition - peering improvement and node operations improvement
- **Open Forum**  
  - Chitchat calendar invite for the Besu group in Discord (every week after our Contributor Call)
- **Future Topics**

  

    **|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155691/GMT20220705-150521_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155691&fileName=GMT20220705-150521_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155691&fileName=GMT20220705-150521_Recording.transcript.vtt) | File [GMT20220705-150521\_Recording.transcript.vtt](/wiki/download/attachments/22155691/GMT20220705-150521_Recording.transcript.vtt?api=v2) | Jul 07, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155691/GMT20220705-150521_Recording.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155691&fileName=GMT20220705-150521_Recording.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155691&fileName=GMT20220705-150521_Recording.txt) | Text File [GMT20220705-150521\_Recording.txt](/wiki/download/attachments/22155691/GMT20220705-150521_Recording.txt?api=v2) | Jul 07, 2022 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

[Download All](/wiki/download/all_attachments?pageId=22155691)**