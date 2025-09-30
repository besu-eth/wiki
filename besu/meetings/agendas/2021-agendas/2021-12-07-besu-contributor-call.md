# 2021-12-07 Besu Contributor Call

(Meeting Link: ⁨[https://consensys.zoom.us/j/94665568300](https://consensys.zoom.us/j/94665568300)[⁩]) 

APAC/AMER Friendly Time -  0100UTC ([https://www.timeanddate.com/worldclock/converter.html?iso=20210913T010000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20210913T010000&p1=224&p2=179&p3=1440&p4=195&p5=47))

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
  - Proposed additional maintainers: 
    - Frank Li [https://github.com/hyperledger/besu/pull/3120](https://github.com/hyperledger/besu/pull/3120)
- **Release updates**
  - Release process in general, plan for diversifying who can make a release.([Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence) )
    - How many maintainers required to sign off on a release?
  - GAR-E - what does it still need to reduce friction? - currently GAR-E is proprietary. Outside maintainers currently need to use a checklist and do it manually.
  - What role (if any) does CircleCI have in releasing?
- **Work Updates**
  - Static code analysis ([Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence))
    - Example output here: [https://sonarcloud.io/dashboard?id=hyperledger-cicd\_besu](https://sonarcloud.io/dashboard?id=hyperledger-cicd_besu)
    - Can we get it to run for non-maintainers (uses a restricted context)
    - Can we get the coverage output combined across reference tests, acceptance tests, unit tests
    - Still need to add some exclusions - eg acceptance test code is being flagged as uncovered
  - Matrix/Rocketchat discussion
    - asking the community ([Grace Hartley (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/5c3e0cd1ff324728a1db2448?ref=confluence))
    - Fill the survey  - [Hyperledger Community Chat Taskforce](https://lf-hyperledger.atlassian.net/wiki/spaces/TF/pages/20873773/Hyperledger+Community+Chat+Taskforce)
  - Ongoing Vert.x upgrade [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence)
- **Other Business** 
- **Open Forum**
  - updates on Coding conventions (var, varargs, etc)
    - currently we "use it where it makes sense" 
    - but don't mandate it
    - would be great if someone would update the coding conventions doc

  

**View recording:**

no recording this time