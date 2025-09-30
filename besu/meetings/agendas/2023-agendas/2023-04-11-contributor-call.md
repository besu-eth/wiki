# 2023-04-11 Contributor Call

(Meeting Link: ⁨[https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09](https://zoom.us/j/97540031823?pwd=dEJrRW1LakFlWnZPelI3VGxoVjg2dz09))

EMEA Friendly Time ([https://www.timeanddate.com/worldclock/converter.html?iso=20230412T160000&p1=224&p2=179&p3=1440&p4=195&p5=47](https://www.timeanddate.com/worldclock/converter.html?iso=20230412T160000&p1=224&p2=179&p3=1440&p4=195&p5=47))

- 9 am Tuesday Los Angeles time
- 12 am Tuesday New York time
- 18h Tuesday Paris time

**Agenda**

-  **Housekeeping**
  - Antitrust notice - [https://www.linuxfoundation.org/antitrust-policy/](https://www.linuxfoundation.org/antitrust-policy/)
  - This meeting is being recorded
  - Please Mute unless speaking
  - If you have a question use the raise hand feature
- **General Announcements**
  - HL GitHub Runner limits ([Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence) ) - Consensys currently has a handful of EC2 instances augmenting the build load for amd64 and docker processes.  Discuss a permanent solution.  
    - runner arch requirements: arm64 runners, docker runners, amd64 runners
    - cost versus upgrading github plan
- **Release updates**
  - 23.1.3 hotfix release, tentatively to re-build and re-deploy to include hotfix for bonsai 
    - [5321](https://github.com/hyperledger/besu/pull/5321) hotfix for execution payloads with disjoint validator indices, noticed in rare cases with nimbus CL combo
    - [5330](https://github.com/hyperledger/besu/pull/5330) hotfix for bonsai relating to EIP-158
  - 23.4.0-RC1 delayed until after shapella, just to prevent confusion and risk about shapella readiness.  Highlights include
    - rocksdb 8.0 [#5262](https://github.com/hyperledger/besu/pull/5262)
    - transaction pool layering [#5290](https://github.com/hyperledger/besu/pull/5290)
    - dagger inroads [#5244](https://github.com/hyperledger/besu/pull/5244)
- **Work Updates**
  - inversion of control / decoupling - update from [Justin Florentine](https://lf-hyperledger.atlassian.net/wiki/people/712020:71871f91-9632-4415-9d78-780eb53fd275?ref=confluence) 
  - update on postman docs site [Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence) 
  - Mega-EOF [Danno Ferrin](https://lf-hyperledger.atlassian.net/wiki/people/5b7f2d80c4e4892a5b789551?ref=confluence) 
    - Will work on separate branch in the Besu repo.
- **Other Business**
  - RFC - [Proposal: Replace Quarterly and Bi-Weekly with Monthly Releases](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Proposal%3A+Replace+Quarterly+and+Bi-Weekly+with+Monthly+Releases)
- **Metrics Review -** [https://insights.lfx.linuxfoundation.org/projects/hyperledger/besu/dashboard;quicktime=time\_filter\_3Y](https://insights.lfx.linuxfoundation.org/projects/hyperledger%2Fbesu/dashboard;quicktime=time_filter_3Y)
- **Roadmap Review - [Roadmap](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Roadmap) - roadmap pending proposal and discussion**
- **Open Forum - skipped**
- **Future Topics - skipped**

### Recording

[https://youtu.be/yV7A0t-IgCM](https://youtu.be/yV7A0t-IgCM)