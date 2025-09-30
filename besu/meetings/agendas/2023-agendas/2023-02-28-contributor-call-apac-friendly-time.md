# 2023-02-28 Contributor Call - APAC Friendly Time

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
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - /add item/
- **Roadmap Review** 
  - [Besu Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap)
- **Release updates**
  - [Release Rotations 2023](../../../../besu/developing-and-conventions/releasing/archive/release-rotations-2023.md)  
  - [23.1.1 proposed for March 8](https://discord.com/channels/905194001349627914/943252457063075880/1078415059493060628) - thoughts?
    - Ideally would include Goerli Shanghai config
    - No objections to March 8 release date
- **Work Updates**
  - Shanghai Epic: [https://github.com/hyperledger/besu/issues/4746](https://github.com/hyperledger/besu/issues/4746)
    - Ready for Sepolia and on track for mainnet
  - Work started on **EIP-6110: in-protocol deposits** by external contributor [https://github.com/hyperledger/besu/pull/5055](https://github.com/hyperledger/besu/pull/5055)
    - Appears to be done as part of the Ethereum Protocol Fellowship by Mikhail's mentee: [https://hackmd.io/@doPpmyH4Ta-4Yc8pq3u-ZA/BkQKSAn2s](https://hackmd.io/@doPpmyH4Ta-4Yc8pq3u-ZA/BkQKSAn2s)
    - Any reason not to include this on main using ExperimentEipsTime as a feature toggle?
      - Have further discussion on contributor discord
- **Other Business**
  - merge queue - any objections to enabling this?
    - the only change to how we currently work is you would have to manually squash commits on your branch PR rather than via the github UI - eg [https://stackoverflow.com/questions/25356810/git-how-to-squash-all-commits-on-branch](https://stackoverflow.com/questions/25356810/git-how-to-squash-all-commits-on-branch)
    - Sally has tested it out on a couple of repos - notes here [https://github.com/hyperledger/besu/issues/5102](https://github.com/hyperledger/besu/issues/5102) - I haven't come across any showstoppers
    - it's essentially the same as enabling auto-merge, except that any additional "merge from main" actions are automated
    - should reduce our CI spend, as well as reducing manual interventions
    - Outcome: No objections. Sally to enable it after the next release with notes on squash merge instructions
  - Final call to remove #besu-nodes Discord channel.
    - Previously mentioned [2022-12-06 Contributor Call - APAC Friendly Time](../../agendas/2022-agendas/2022-12-06-contributor-call-apac-friendly-time.md)
    - Discussion: [https://discord.com/channels/905194001349627914/905205502940696607/1044723284597559298](https://discord.com/channels/905194001349627914/905205502940696607/1044723284597559298)  
[https://discord.com/channels/905194001349627914/905205502940696607/1044756214669643856](https://discord.com/channels/905194001349627914/905205502940696607/1044756214669643856)
    - One way would be give a couple of days deprecation and ask users with outstanding questions to move them over to #besu
    - Outcome: Simon to ping Danno on concerns re: besu-nodes channel deprecation. No other objections. If objections are resolved then remove the channel.
- **Open Forum**
- **Future Topics**

  

**Recordings**

**[https://youtu.be/5Ek\_B-e-OAU](https://youtu.be/5Ek_B-e-OAU)**

   

|     | File | Modified |
| --- | --- | --- |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22156108/GMT20230228-010007_RecordingnewChat.txt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22156108&fileName=GMT20230228-010007_RecordingnewChat.txt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22156108&fileName=GMT20230228-010007_RecordingnewChat.txt) | Text File [GMT20230228-010007\_RecordingnewChat.txt](/wiki/download/attachments/22156108/GMT20230228-010007_RecordingnewChat.txt?api=v2) | Feb 28, 2023 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |
| Labels<br><br>- No labels<br>- [Edit Labels](#)<br><br>[Preview] [View](/wiki/download/attachments/22156108/GMT20230228-010007_Recording.transcript.vtt?version=1) [Properties](/wiki/pages/editattachment.action?pageId=22156108&fileName=GMT20230228-010007_Recording.transcript.vtt&isFromPageView=true) [Delete](/wiki/pages/confirmattachmentremoval.action?pageId=22156108&fileName=GMT20230228-010007_Recording.transcript.vtt) | File [GMT20230228-010007\_Recording.transcript.vtt](/wiki/download/attachments/22156108/GMT20230228-010007_Recording.transcript.vtt?api=v2) | Feb 28, 2023 by [Ry Jones](/wiki/people/557058:078cecfc-fb17-4d9a-8759-b5b74efa6850) |

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description  

</form> </div> </div> <div> <a class="download-all-link" href="/wiki/download/all\_attachments?pageId=22156108" title="Download all the latest versions of attachments on this content as single zip file.">Download All</a> </div> </div> <p /></x-turndown>