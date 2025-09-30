# 2023-11-07 Contributor Call - APAC Friendly Time

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
  - A few of us are attending devconnect, please reach out on Discord if you would like to join us there
- **Release updates**
  - Next release 23.10.2
    - Besu quite stable, good time to do a release before big changes are brought in
    - Bring up discussion in the release channel
- **Work Updates**
  - Snap sync server
    - Besu to Besu is syncing well
    - Geth and Nethermind not syncing well
    - Focussing on getting Geth syncing working
  - Upcoming database changes
    - Storing code by code hash instead of account hash
      - Will require running a subcommand to convert an existing database
    - Fully flattened database
      - Want to make the default
      - Will have a conversion tool to convert to the new format
    - After these changes along with snap sync, we will be able to move Besu to use Bonsai as the default/primary storage mechanism
    - Matt Nelson has started discussions on private networks using Bonsai
    - Investigation on trie logs using blob DB
      - Confirming expecting performance improvements
    - Possible we could have a single subcommand to database upgrade the database
- **Other Business**
  - (From Simon) Have marked the [debug proposal as ACCEPTED](https://lf-hyperledger.atlassian.net/wiki/display/BESU/%5BACCEPTED%5D+DEBUG+Log+Improvement+Proposal) and incorporated into [Coding Conventions#Logging](../../../../besu/developing-and-conventions/coding-conventions.md)
- **Open Forum**
  - /add item/
- **Future Topics**
  - /add item/

  

**Recordings**

  

Playlist: [https://www.youtube.com/playlist?list=PL0MZ85B\_96CHpqsKmljUK8HB98wK67RjC](https://www.youtube.com/playlist?list=PL0MZ85B_96CHpqsKmljUK8HB98wK67RjC)

   

|     | File | Modified |
| --- | --- | --- |

No files shared here yet.

- Drag and drop to upload or [browse for files] ![](/wiki/images/icons/wait.gif)

Upload file 

File description