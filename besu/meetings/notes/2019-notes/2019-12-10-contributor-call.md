# 2019-12-10 Contributor Call

Meeting Video: [dummyfile.txt](#)

Housekeeping

General Announcements

Release Updates

- 1.3.6
- Discussed 1.4 beta release proposal
  - Beta vs rc?
  - HLP [Release Taxonomy](https://lf-hyperledger.atlassian.net/wiki/spaces/TSC/pages/21430846/Release+Taxonomy)
  - Branches for 1.3 maintenance if needed and 1.4 for 1.4.0
  - Master for 1.3.7, 1.4 beta, and 1.4.1
  - rc 13 Feb 2020, full release on 27 Feb 2020
  - 1.3.8 becomes 1.4.0-beta 15 Jan 2020
  - Beta 2 if needed on 29 Jan
  - 1.4-RC on 13 Feb 2020
  - 1.40 targeted at 27 Feb 2020
  - Build version becomes 1.4.0-beta-SNAPSHOT right after 1.3.7 release

Work Updates

- Change Log
  - Only include PRs that have useful changes rather than a line for each PR
  - Either
    - Add a CHANGELOG section to each PR
    - Use a wiki page.
  - Can we keep the changelog in the wiki and not keep it in the codebase?
  - Why not have updating the change log as part of the PR?
    - There will always be merge conflicts
  - Whatever change happens will require an adjustment of habits.
  - Proposal: Make an actual change to the PR as part of the log
    - Standalone commit
    - Or as part of the changes
  - We will try this for the next release or so.
    - Someone will need to review and ensure this is being practiced.
    - Add to contributor guidelines 
- Custom RPC endpoints plugin service

Other Business

- Edward Mack as Maintainer.
- CI/CD
  - Jenkins is dead.
  - Circle CI for everything.
  - It has the most scope for being faster compared to all other CI systems we have looked at
  - Working on posting build failures to rocket chat
  - All infrastructure and tooling is on HLP owned/operated
  - Zero servers owned by ConsenSys

Open Forum

Next Meeting - 7 Jan 2020 - EMEA/AMER time

Action Items

 - Madeline to update contributor guidelines to reflect Change Log and communicate.