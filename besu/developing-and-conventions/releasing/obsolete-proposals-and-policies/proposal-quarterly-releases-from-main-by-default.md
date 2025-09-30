# Proposal: Quarterly releases from main by default

This is a refinement to the proposal: [Avoid Cherry Picked Releases](https://lf-hyperledger.atlassian.net/wiki/display/BESU/Proposal%3A+Avoid+Cherry+Picked+Releases)

## **Goal:** Make releasing as easy as possible  
  

## **Suggested Solution:** Don't use RCs for Quarterly releases (by default)

- We sometimes already do this, for example with 23.7.0.
- We can still soak for a longer period of time than normal for riskier changes and we can advertise our soak to beta testers if we wish.
- We can still use a release branch if we feel the need, this proposal just suggests *by default*  we try to release from main.
- There is no need for this proposal to change the concept or versioning of quarterly releases and what they might signal (more significant changes).

## **What needs to change?**

Some sort of notification about **upcoming** breaking changes, the obvious place being in the changelog/release notes **ahead** of the change landing.

## **Suggested Deprecation Policy**

- Have an "Upcoming breaking changes" section in the changelog, which announces features that are upcoming, e.g. a warning about big changes in the next quarterly release.
- Time it needs to be in changelog before releasing is at maintainers' discretion.
- Feature/branch/PR management of upcoming feature is at maintainers' discretion.
- Optionally add target release/date.