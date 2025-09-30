# Fixing DCO on main/release

A maintainer with [Admin](https://github.com/orgs/hyperledger/teams/besu-admin/members) access to the repository is required to fix the main repo:

1. Clone an up-to-date version of the broken branch
2. `git commit --amend` `--signoff`  and ensure the appropriate Sign-off is included in the commit message
3. Visit [https://github.com/hyperledger/besu/settings/branches](https://github.com/hyperledger/besu/settings/branches) and change the glob to no-longer match the branch that is about to be force-pushed to
4. `git push --force-with-lease origin main` 
5. Return the branch protection glob to the old value
6. Announce the change in the [contributors channel](https://chat.hyperledger.org/channel/besu-contributors) a message like "The head of \`main\` branch for repository \`hyperledger/besu\` has been rebased to deal with a DCO issue, please follow the instructions on [Fixing DCO on main/release](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/pages/22154247/Fixing+DCO+on+main+release) to fix your local repositories"

For everyone else (only required if you were unlucky enough to check out the commit with the broken DCO) to fix your local repo:

1. `git fetch origin`
2. `git branch -f main origin/main` if your local main is based off the upstream main`   `
3. (*Optionally*) `git push --force FORK main` if you are keeping your fork's main up-to-date
4. For all branches based on the bad checkout:
  1. `git checkout $BRANCH` 
  2. `git rebase --interactive main` 
  3. Remove the old main commit from the list

Sometimes you might get DCO issues on a release branch when you're merging new commits in, fix it following a similar process:

1. `git checkout release-22.1.x` to checkout the release branch at the last release
2. `git merge main` to merge in desired commits (use git reset --hard xxxx to set main at a desired commit)
3. `git rebase -i HEAD~10` to initiate a interactive rebase, replace 10 with the number of commits back that has DCO issues
4. In the rebase file find the commit hashes with DCO issues, replace the '`pick`' with '`edit`'
5. You might also need to fix some merge conflicts as the rebase happens, should be straight forward
6. When the rebase stops at your desired commits, run `git commit --amend --no-edit --signoff to signoff` the commit
7. Run `git rebase --continue` to continue, repeat steps 5-6 until done
8. Push the changes with `git push --force-with-lease origin release-22.1.2`