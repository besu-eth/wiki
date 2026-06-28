All code submitted to Besu must have a [Developer Certificate of Origin](https://developercertificate.org/) (DCO) sign-off. This page covers how to sign off your commits and what to do when the DCO check fails.

For the short version, see [`DCO.md`](https://github.com/besu-eth/besu/blob/main/DCO.md) in the main repository.

## When committing

Every commit message needs a line like `Signed-off-by: Your Legal Name <your-email@address>`. You could add it manually each time, but it's easier to automate:

1. Set your legal name in the git configuration:

   ```bash
   git config user.name "Legal Name"
   ```

2. Set your email in the git configuration:

   ```bash
   git config user.email "email@address"
   ```

3. Add `-s` (or `--signoff`) to all your `git commit` invocations. To avoid typing it every time, add a git alias:

   ```bash
   git config --global alias.c 'commit --signoff'
   ```

   Then run `git c` instead of `git commit`. Most IDEs (such as IntelliJ IDEA) also have a "Sign-off commit" option in their commit dialog.

If you use the GitHub web UI for commits, make sure the `Signed-off-by` line uses the same email address as the commit author. You can use your GitHub `noreply` email address (`username@users.noreply.github.com`) if you keep your email private.

## When merging

The merge of a PR must also carry a sign-off so the entire repository is known to be under the associated license. When merging a pull request through **Squash and merge**, there must be a `Signed-off-by` line for every contributor, plus one for you as the person merging; just make sure you don't delete them.

## When the DCO check fails on your PR

If the DCO check fails on your pull request, open the check's **Details** link and follow the instructions. In most cases the failure means one or more commits are missing a `Signed-off-by` line.

To add a sign-off to the most recent commit:

```bash
git commit --amend --signoff
```

To add sign-offs across several commits, use an interactive rebase, mark the offending commits as `edit`, and run `git commit --amend --no-edit --signoff` at each stop before continuing with `git rebase --continue`.

After amending or rebasing, force-push your branch:

```bash
git push --force-with-lease
```

## Fixing DCO on main or a release branch

> [!NOTE]
> This procedure requires a maintainer with admin access to the repository and a force-push to a protected branch. It should only be needed in rare cases where a commit missing a sign-off reached `main` or a release branch.

A maintainer with admin access fixes the upstream branch:

1. Clone an up-to-date version of the broken branch.
2. Run `git commit --amend --signoff` and ensure the appropriate sign-off is included in the commit message.
3. Temporarily change the [branch protection](https://github.com/besu-eth/besu/settings/branches) glob so it no longer matches the branch about to be force-pushed.
4. Force-push:

   ```bash
   git push --force-with-lease origin main
   ```

5. Restore the branch protection glob to its previous value.
6. Announce the change in the contributors channel on [Discord](https://discord.com/invite/hyperledger), for example: "The head of `main` for `besu-eth/besu` has been rebased to deal with a DCO issue; please follow the instructions on the Working with DCO wiki page to fix your local repositories."

Everyone else (only required if you were unlucky enough to check out the commit with the broken DCO) fixes their local repo:

1. `git fetch origin`
2. `git branch -f main origin/main` if your local `main` is based off the upstream `main`.
3. (Optionally) `git push --force FORK main` if you keep your fork's `main` up to date.
4. For all branches based on the bad checkout:
   1. `git checkout $BRANCH`
   2. `git rebase --interactive main`
   3. Remove the old `main` commit from the list.

If you get a DCO issue on a release branch while merging new commits in, fix it with a similar process:

1. `git checkout release-x.y.z` to check out the release branch.
2. `git merge main` to merge in the desired commits.
3. `git rebase -i HEAD~10` to start an interactive rebase (replace `10` with the number of commits back that have DCO issues).
4. In the rebase file, find the commits with DCO issues and replace `pick` with `edit`.
5. Resolve any merge conflicts as the rebase proceeds.
6. When the rebase stops at each commit, run `git commit --amend --no-edit --signoff`.
7. Run `git rebase --continue`, repeating steps 5-6 until done.
8. Push the changes with `git push --force-with-lease origin release-x.y.z`.

## Why?

Per the [Linux Foundation Decentralized Trust (LF Decentralized Trust) charter](https://www.lfdecentralizedtrust.org/about/charter), all code submitted to the project needs a [Developer Certificate of Origin](https://developercertificate.org/) (DCO) sign-off. This certifies that you are able to submit your contribution under the license of the repository, and for it to be redistributed under that same license.

You "sign" this certificate by including a `Signed-off-by: Legal Name <email-address>` line in your git commit, using the email address associated with your GitHub account.

If you have any questions, you can reach us on [Discord](https://discord.com/invite/hyperledger).
