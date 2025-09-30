# Fixing DCO on master/release-

As a maintainer with Admin access to the repository:

1. Clone an up-to-date version of the broken branch
2. `git commit --ammend` `--signoff`  and ensure the appropriate Sign-off is included in the commit message
3. Visit [https://github.com/hyperledger/besu/settings/branches](https://github.com/hyperledger/besu/settings/branches) and change the glob to no-longer match the branch that is about to be force-pushed to
4. `git push --force-with-lease origin master` 
5. Return the branch protection glob to the old value
6. Announce the change in the [contributors channel](https://chat.hyperledger.org/channel/besu-contributors) a message like "The head of \`master\` branch for repository \`hyperledger/besu\` has been rebased to deal with a DCO issue, please follow the instructions on [Fixing DCO on master/release-](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154038/Fixing+DCO+on+master+release-) to fix your local repositories"

For everyone else:

1. `git fetch origin`
2. `git branch -f master origin/master` if your local master is based off the upstream master`   `
3. (*Optionally*) `git push --force FORK master` if you are keeping your fork's master up-to-date
4. For all branches based on the bad checkout:
  1. `git checkout $BRANCH` 
  2. `git rebase --interactive master` 
  3. Remove the old master commit from the list