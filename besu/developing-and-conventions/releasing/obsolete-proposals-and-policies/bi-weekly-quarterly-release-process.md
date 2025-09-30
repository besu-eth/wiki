# Bi-Weekly & Quarterly Release Process

During the [August 4th Contributor Call](https://lf-hyperledger.atlassian.net/wiki/display/BESU/2020-08-04+Contributor+Call+Agenda), Besu's release process was discussed.   
  
Over the past few months, every Besu release has required a release candidate (see the original [proposal](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Proposal%3A+Create+a+Release+Candidate+for+every+release)). This change was implemented at a time where Besu releases had run into several showstopper bugs.   
Since then, things have stabilized. Since June, there hasn't been a bug found in a Besu RC requiring we scrub or re-do the release.   
  
In order to streamline the release process, on the last contributor call, we agreed to the following proposal:  
  
**Bi-Weekly Releases:**  

- No RC, release directly off master branch
- Before the release is promoted by contributors' organizations, we recommend they:
  - Run it for 24 hours against the Ethereum mainnet network at the head of the chain, and;
  - Complete a fast sync from scratch against one of the major Ethereum testnets (i.e. Ropsten). 
- If issues are found with the release during the release process (e.g. failing acceptance test), we:
  - Scrub the release, meaning we do not complete the process and make it available;
  - Re-use the same release number at the next bi-weekly release given it was never on a public release.
- If issues are found with the release after the release process (e.g. issues processing blocks on mainnet once nodes are updated), we:
  - We recommend people not use it and stop promoting it;
  - We investigate the issue and potentially have an out-of-cycle release if maintainers judge the issue serious enough to do so;  
  - Have the next release (whether in-cycle or not) on an incremented version (e.g. if the scrubbed release is 1.1.1, the next one should still be 1.1.2) 

**Quarterly Releases:**  

- We cut RCs off a separate branch.
  - We aim to have two RCs before a quarterly release to allow bug fixes from RC1 to be included in RC2. 
- Before the release is promoted by contributors' organizations, we recommend they:
  - Run it for 48 hours against the Ethereum mainnet network at the head of the chain, and;
  - Complete a fast sync from scratch against the Ethereum mainnet.