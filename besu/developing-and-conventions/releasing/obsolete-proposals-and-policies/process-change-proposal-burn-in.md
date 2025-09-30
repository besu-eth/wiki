# Process change proposal: burn-in

Draft process based on discussions from discord - edits welcome

# Burn-in

# ![](https://media.discordapp.net/attachments/905205502940696607/1049801866474696734/unknown.png?width=1440&height=499)

Start the pre-release process on Friday (n-5) instead of Wednesday, to allow time for the burn in process.

All PRs for the release need to be merged by Friday.

# Vote

While the burn-in is happening, maintainers and community have 3-4 days (2 business days) to find a reason to object.

Start a thread in besu-release channel

If any one party formally objects then a formal vote is required. At least 24 hours is required for a vote to close, and a scheduled release can be delayed for the vote.

## Who can object?

Currently - besu maintainers

besu-release channel is public so any community member can comment

## How to object?

in besu-release channel or 'the agreed communication channels'

  

It’s already the case that if burn-in testing fails, the release can be delayed or skipped.

The final stage of the release is making it public, applying tags etc and announcing it.

  

# Technical details to be worked out

 re:branching, tagging - Friday we update the version in gradle.properties to the release version, briefly, then update to snapshot. We would have to do something about the docker latest tag, but we would not introduce additional processes like tagging. Wednesday "releases" would be limited to publishing a github release and official docker images for the version

  

I think ideally we would not publish docker version numbers until the official release date. latest seems to be the highest risk for unintentional upgrades. Having a separate action to publish docker images seems error prone - I suspect we can find a way to automatically gate that.

Because there are keys needed to move docker tags and publish, GHA seems the best place to put it for "on demand" use. Plus it comes with a who/when audit trail.

  

GHA - could implement this via a draft release, i believe there is an event type emitted for that. the application of release tags could be isolated to a workflow that just promotes from draft, using those tags