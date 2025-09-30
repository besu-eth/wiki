# Proposal: Avoid Cherry Picked Releases

This was previously a proposal to "*Replace Quarterly and Bi-Weekly With Monthly Releases*" but I think I was putting the cart before the horses: it was proposing one potential specific solution instead of starting a discussion about the problem.

## **Goal:** Make releasing as easy as possible

The main time sink for our releases is cherry-picking. There are two scenarios where we cherry-pick:

1. Adding to an existing RC branch during quarterly releases
2. Adding hotfixes to a point release

In both cases we have to do this because "unstable" commits are blocking releasing from the main branch.

## **Suggested Solution:** Keep main branch releasable

If we are confident about the stability of the main branch then we can be flexible with our release schedule.  
  
There are many details we could discuss further such as deprecation policy, feature toggles, improved regression testing, and burn-in procedure, but will focus on getting buy-in for the main point of this proposal first.  
  
I will mention one interesting suggestion Gary made that we could treat our (currently internal) burn-in period as a beta release that is announced. We may then gain a better diversity of testing from the community, which is one benefit of the quarterly release candidates (that we don't particularly utilise currently).

## **Suggested Deprecation Policy**

- Have an "Upcoming breaking changes" section in the changelog, which announces features that would have otherwise gone in a quarterly release.
- Time it needs to be in changelog before releasing is at maintainers' discretion.
- Feature/branch/PR management of upcoming feature is at maintainers' discretion.
- Optionally add target release/date.

### **Discussion**

Discussion points from [last call](https://lf-hyperledger.atlassian.net/wiki/display/BESU/2023-05-09+Contributor+Call) and my responses from Discord, copied from [#besu-release](https://discord.com/channels/905194001349627914/943252457063075880/1106103888840495175). **Some questions outstanding**...  
  

> Thanks for your feedback so far. It sounded like there was some partial agreement on at least removing the RC process, which I think would alleviate most of the release pain points. I'd like to address some specific points:
> 
> [Danno Ferrin](https://lf-hyperledger.atlassian.net/wiki/people/5b7f2d80c4e4892a5b789551?ref=confluence)  *“you have to freeze people out of submitting things to mainline and that’s very problematic”*  
> [Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence)  *“I agree”*
> 
> Definitely want to dig into this more. I agree it may require some changes to how we work compared to before but there are usually ways around it. Have you got some specific examples where you have needed to merge not-yet-releasable commits to main or an RC branch?
> 
> [Gary Schulte](https://lf-hyperledger.atlassian.net/wiki/people/6047b948b020eb00684030b6?ref=confluence) *"Cherry picks and RCs are a useful process to have"*
> 
> Can you give some examples of when it is useful please?
> 
> To be clear the proposal it to avoid cherry-picking (by default), not ban it. I expect we would be pragmatic in hot-fix scenarios.   
> I don’t think there’s anything stopping us from creating a release branch off the release tag and hot-fixing on that, should the need arise and we’re not confident in forward fixing for whatever reason.
> 
> Overall and long-term though, I think it makes our lives a lot easier if we can rely on main branch being releasable without having to do days of testing on a bunch of changes.  
> To enable this, either we could extensively manually test PRs (which we mostly do already) or we could improve our regression tests (or have better support/integration for hive regression tests).  
> Both of these cost time and effort. I prefer the latter since it’s a long term investment that eventually reduces the need for most manual tests.   
>   
>   
> [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence)  *“agree with ‘keep main releasable’ but don’t want to create a situation where we are reverting PRs as a counter to the RC process"*
> 
> Absolutely agree we shouldn’t put ourselves in a situation where we are more likely to need to revert commits. I think the simple short term solution is to ensure PRs are well tested before they are merged which hopefully we are doing anyway, rather than relying on the RC process that can sometimes come weeks after the buggy commit has merged.   
>   
>   
> [Danno Ferrin](https://lf-hyperledger.atlassian.net/wiki/people/5b7f2d80c4e4892a5b789551?ref=confluence)  *“Governance on who decides when”*
> 
> Agree, I’m in favour of keeping a transparent release process, and we might not even need to come to consensus on release date everytime…   
>   
>   
> [Matt Nelson (Deactivated)](https://lf-hyperledger.atlassian.net/wiki/people/6092a453afcdb700691fdc3b?ref=confluence) *“currently bi-weekly removes need for arbiter”*
> 
> This is actually why I originally suggested “at least a monthly release” so that we still had a regular cadence/expectation like the bi-weekly releases. Nothing stopping us from keeping the bi-weekly release cadence either, it would just be from main by default ideally IMO.