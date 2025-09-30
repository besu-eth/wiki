# Off-cycle release process

# Context

Inevitably, there will be a need to release immediately, regardless of plans. Should an emergency, critical bug, or security issue (or any matter of that sort) arise, the following process will govern the release.

  

An off-cycle release is defined as: 

- A release outside of the scheduled times [here](../releasing/release-rotations-2024.md)
- A release not on the typical Wednesday or Thursday slots
- A cherry-picked release (not off main branch)

Process: 

- Any besu contributor may bring forth the need for an off-cycle release
  - including justification of why the release is warranted
  - via the **besu-contributors** channel in Discord
- Scope for the release also needs to be agreed.
  - via the **besu-release** channel in Discord
- Ideally, consensus is reached. Allow a 48 hour voting period to allow for objections. 
  - Justification must be given if objecting to the release
  - If there are no objections, the release can continue at an agreed upon time.
  - Any objection and the justification given must be seriously considered and weighed against the reasons for the release.
  - This discussion must happen in the **besu-release** channel in Discord.

Justification for release (examples)

- critical bug affecting a number of users which requires a patch
- regular release process will not address the issue in time
- urgent security issue discovered

Justification for objection (examples)

- technology X introduced is bad for Y reasons