# GitHub Merge Queue

**Update** - disabled Feb 14 2025

- branch protection (rulesets) set back to previous ie
  - combined main + release\*
  - disallow force pushes to any branches

Issues found

- still runs all the checks (GHA) on merge group (PR enters merge queue) even if the PR is up to date - so we double up on CI - I think even if the queue is empty, definitely if a PR is removed from the queue
  - [https://github.com/orgs/community/discussions/43988](https://github.com/orgs/community/discussions/43988) - the issue has been closed and is apparently “exploratory” → [https://github.com/github/roadmap/issues/824#issuecomment-2501843484](https://github.com/github/roadmap/issues/824#issuecomment-2501843484)
- GHA status not reported even though all workflows are complete and appear successful
  - maybe this? [https://github.com/orgs/community/discussions/64027](https://github.com/orgs/community/discussions/64027)
- had to alter branch protection rules - merge queue creates temporary branches with a special prefix to validate pull request changes and we had a catchall branch protection disallowing force pushes to any branches. [more info](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue#how-merge-queues-work)
- had to add “on merge” event for [GHA workflows](https://github.com/hyperledger/besu/pull/8303) to be able to run required checks - [more info](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue#triggering-merge-group-checks-with-third-party-ci-providers)

**Update** - Tried merge queue again since it’s out of beta and there’s a lot of approved PRs to merge

Action plan to try the experiment:

- enable merge queue on besu
  - you can't enable it on rulesets with `*` match so would need to duplicate the ruleset - have a separate one for `release*`
- merge this PR [#8284](https://github.com/hyperledger/besu/pull/8284) which hopefully will help with flaky ATs
- add a bunch of other PRs to merge queue - we live with the merge commit message being the PR description - there's [10 approved](https://github.com/hyperledger/besu/pulls?q=sort%3Aupdated-desc+is%3Apr+is%3Aopen+review%3Aapproved)
  - would exclude the [maintainer update](https://github.com/hyperledger/besu/pull/8230) - still voting
  - also the [BadBlockManager](https://github.com/hyperledger/besu/pull/8207) - has an open q
  -  the [gas limit one](https://github.com/hyperledger/besu/pull/8249) ? still has some open q's
  - so there's 7 to merge
- if it doesn't work (only problem I see being flaky tests mean merge queue doesn't help), can switch off merge queue again - back to status quo

**Update -** disabled ~ Mar 17 2023

Issues found

- still runs all the checks (including GHA) again even if the queue is empty [https://github.com/orgs/community/discussions/46757?sort=top#discussioncomment-4912738](https://github.com/orgs/community/discussions/46757?sort=top#discussioncomment-4912738)
- GH enforcing the max 20 runners at once limit, which they never did before 
- hence PRs were being silently removed from the queue (GHA not reporting status) and no benefit was being gained from the queue

**Update** - enabled on Mar 13 2023. DCO required adjusting as per [https://github.com/hyperledger/besu/pull/5207](https://github.com/hyperledger/besu/pull/5207). 

Essentially this works the same as enabling auto-merge, except that any additional "merge from main" actions are automated.

**Impacts on current workflow**

- once the merge queue is enabled, it's a requirement - so all PRs will be merged via the queue.
- to add your PR to the merge queue, you need to click the green "merge when ready" button" just as you would click the "enable auto-merge" button
- "squash merge commits" is done automatically
  - with the commit message = PR title (full commit details still available in the PR)
  - ~so if you want to edit the commit message, you'll need to do this locally on your branch prior to adding it to the merge queue - eg~ [~https://stackoverflow.com/questions/25356810/git-how-to-squash-all-commits-on-branch~](https://stackoverflow.com/questions/25356810/git-how-to-squash-all-commits-on-branch)
- avoiding unnecessary merge conflicts - think about inserting into a sensible place in the changelog, rather than appending to the end by default
- when there's a merge conflict, the PR with the conflicts gets kicked out of the merge queue and manual intervention is required - same as if you had enabled "auto-merge"

Discussion in Feb 28 contributor call on enabling the merge queue [2023-02-28 Contributor Call - APAC Friendly Time](../../../besu/meetings/agendas/2023-agendas/2023-02-28-contributor-call-apac-friendly-time.md) after 23.1.1 release

Note - it's part of "branch protection" - so you turn it on for specific branch protection rules.

This feature is still in beta - discussion [https://github.blog/changelog/2023-02-08-pull-request-merge-queue-public-beta/](https://github.blog/changelog/2023-02-08-pull-request-merge-queue-public-beta/)

Link to Besu merge queue (when enabled) would be [https://github.com/hyperledger/besu/queue/main](https://github.com/hyperledger/besu/queue/main)