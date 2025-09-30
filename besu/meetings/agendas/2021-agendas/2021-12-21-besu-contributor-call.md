# 2021-12-21 Besu Contributor Call

(Meeting Link: ⁨[https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09](https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09))

EMEA/AMER Friendly Time -  ([https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20201012T150000&p1=224&p2=179&p3=1440&p4=195&p5=47))

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

**Discussion:**

Besu Incentive Program

- Goals 
  - Teams free to do what they want with validator value and validator tx fees (rewards) 
  - Keys will be divested over 6 month periods (allowing more and more funds to be withdrawn) 
- Provide long-term incentives to folks that are building Ethereum Mainnet clients 
- Offered to all mainnet client teams (execution and consensus) 
- EF will provide validator keys at a later time depending on incentive program milestones
- Performance metrics
  - Taken over a monthly time frame
- Over 95% attestation and block proposal inclusions 
- Avoid slashing for these validators - slashed validators will be removed from the program
- Consensus client issues - EF will not penalize execution layer client for consensus issues on the other client 
- Execution layer has to be quick enough (performant) to create the block 
- Interoperability 
  - Trust in this process by EF - good faith interop (could use canary nodes for combinations that are less tested)
- Why Now?
  - Prepping for the Merge
  - Helps measure performance and confirms meeting protocol expectations
- How do we run this program across the Besu community? 
  - This is a big ask for time from community members - Not all should be forced to be node operators
- Concerns are:
  - All maintainers can't run a release 
  - Data not shared from ConsenSys with the community
  - Lack of transparency from ConsenSys team on roadmap
  - Money will make this open source project more challenging with the community 
  - PRs that need to be reviewed in timely manner
- Ideas for Incentivizing Besu community
  - Near term idea: Bounty program
  - Near term idea: Clear benchmarks/requirements for operator validator nodes
  - Medium/long term idea: Besu DAO

**Next Steps:**

1. More detailed document around Incentive Program on Wiki
2. Agenda for next call (potentially off-cycle):
  1. Incentive program (30 mins)
    1. Cost of running nodes
  2. Besu maintainer progress/community concerns (30 mins)

  

  

**Note: We did not have time to address these other items:**

**General Announcements**

- **Release updates**  
  - Release process in general, plan for diversifying who can make a release.([Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence) )
    - How many maintainers required to sign off on a release?
  - GAR-E - what does it still need to reduce friction?
  - What role (if any) does CircleCI have in releasing?
- **Work Updates**
  - Static code analysis ([Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence))
    - Example output here: [https://sonarcloud.io/dashboard?id=hyperledger-cicd\_besu](https://sonarcloud.io/dashboard?id=hyperledger-cicd_besu)
    - How do we know when we should turn on build gating?
  - Matrix/Rocketchat discussion
    - asking the community ([Grace Hartley (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/5c3e0cd1ff324728a1db2448?ref=confluence)) 
    - Fill the survey when is coming out
  - Ongoing Vert.x upgrade [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence)
  - Discussion of the Ethereum Foundation announcement
- **Other Business** 
- **Open Forum**
  - Design process proposal for further modularization:
    - transaction pooling and block building is a hot topic lately. [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence)would like to start a design for factoring out block building much like we did with the EVM. What design artifacts should we produce (if any) prior to submitting PRs?
  - Inactivity clause for moving maintainers to emeritus status - the [current guide](https://github.com/hyperledger/besu/blob/main/MAINTAINERS.md) says a quarter of inactivity. Do we want to extend that? 6 months? Longer? 
> \> A general measure of inactivity will be no commits or code review comments for one reporting quarter, although this will not be strictly enforced if the maintainer expresses a reasonable intent to continue contributing.
- **Future Topics**

  

**View recording:** 

   

|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155110/Besu+PKI+Support.pdf?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155110&fileName=Besu+PKI+Support.pdf&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155110&fileName=Besu+PKI+Support.pdf) | PDF File [Besu PKI Support.pdf](/wiki/download/attachments/22155110/Besu%20PKI%20Support.pdf?api=v2) | Nov 23, 2021 by [Francesco Andreoli](/wiki/people/610104864e8d8d0069291688) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155110/BESU-2021-12-21-Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155110&fileName=BESU-2021-12-21-Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155110&fileName=BESU-2021-12-21-Recording.transcript.vtt) | File [BESU-2021-12-21-Recording.transcript.vtt](/wiki/download/attachments/22155110/BESU-2021-12-21-Recording.transcript.vtt?api=v2) | Dec 21, 2021 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22155110/BESU-2021-12-21-chat.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22155110&fileName=BESU-2021-12-21-chat.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22155110&fileName=BESU-2021-12-21-chat.txt) | Text File [BESU-2021-12-21-chat.txt](/wiki/download/attachments/22155110/BESU-2021-12-21-chat.txt?api=v2) | Dec 21, 2021 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

</form> </div> </div> <div> <a class="download-all-link" href="/wiki/download/all\_attachments?pageId=22155110" title="Download all the latest versions of attachments on this content as single zip file.">Download All</a> </div> </div> <p /><p><span data-colorid="ho7gb13x3n">Passcode:</span><strong><br /></strong></p><p><br /></p></x-turndown>