# DCO

## TL;DR:

If you don't want to break the DCO check, ensure all your commits have signoff.

Git has a built-in mechanism to allow this with the `-s` or `--signoff` argument to `git commit` command, providing your `user.name` and `user.email` have been setup correctly.

git config user.name "FIRST\_NAME LAST\_NAME"  
git config user.email "MY\_NAME@example.com"  
you can also set up a git global alias - see below

If you use GitHub web UI for commits, also ensure you an your email address set as public in your GitHub profile. This avoids issues with `XYZ@users.noreply.github.com` placeholder emails.

# How to work with DCO

## When Committing

You need to ensure that every commit message has a line "`Signed-off-by: Your Legal Name <your-email@address>`", and while you could add that manually every time, here are the steps to follow to automate it:

1. Set your legal name in the git configuration:  
`git config user.name "Legal Name"` 
2. Set your email in the git configuration:  
`git config user.email "email@address"` 
3. Add the `-s`  or `--signoff`  to all `git commit`  invocations.
  1. Add a git alias:  
`git config --global alias.c 'commit --signoff'`  
and then run "`git c`" instead of "`git commit`"
  2. In IntelliJ  
![](./attachments/Screen%20Shot%202019-09-17%20at%2010.13.13%20am.png)

## When Merging

The merge or a PR must also have a DCO so we can know the entire repository is under the associated license.

1. When Merging a Pull Request through **"squash and merge"**, there must be a `Signed-off-by` line for every contributor, and you as the person merging - just make sure you don't delete them ![(smile)](https://lf-hyperledger.atlassian.net/wiki/s/1449019483/6452/ae2804514f9cd9ed0d0281971dae9dc8f3187953/_/images/icons/emoticons/smile.png)
.

## When you have a DCO failure on your PR from DCO Bot

![](./attachments/Screen%20Shot%202019-09-17%20at%208.27.56%20am.png)

'

Click on that "Details" link and follow the instructions.

![](./attachments/Screen%20Shot%202019-09-17%20at%208.28.18%20am.png)

## When you have a DCO failure on your PR from CI

On Circle CI you will see:

![](./attachments/Screen%20Shot%202019-09-17%20at%2012.35.45%20pm.png)

In the full Console Output you will see DCO is checked on ALL branches:

Checking commits in branch origin/main for commits missing DCO... Checking commits in branch origin/merge for commits missing DCO... 11b5f95dd5ef51af398f8b343b266debadd6f0b9 is missing Signed-off-by line. Checking commits in branch origin/pull/2497 for commits missing DCO... Checking commits in branch origin/release-21.10.x for commits missing DCO... Checking commits in branch origin/release-22.1.0 for commits missing DCO... Exited with code exit status 1  

If the commit missing the signoff is on `main` branch, you will need to contact a Besu Maintainer Admin (`main` rebase required).

If the commit missing the signoff is on a non-main branch (eg `merge` in the example above), and you are a Besu maintainer, you should be able to force-push to that branch (eg rollback the most recent commit). 

## Why?

As per section 12.a of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all code submitted to the Hyperledger Foundation needs to have a [Developer Certificate of Origin](http://developercertificate.org/) (DCO) sign-off.

This certifies that you are able to submit your contribution to our repository under the license of the repository, and for the contribution to be redistributed under that same license.

You can "sign" this certificate by including a line in the git commit of "`Signed-off-by: Legal Name <email-address>`", using the email address associated with your GitHub account.

  

* * *

Feel free to [check out this tutorial](https://kauri.io/#single/dco-sign-off--commiting-code-to-hyperledger-besu/) for more help.

  

As per section 12.a of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all code submitted to the Hyperledger Foundation needs to have a [Developer Certificate of Origin](http://developercertificate.org/) (DCO) sign-off.

The sign off needs to be using your legal name, not a pseudonym. Git has a built-in mechanism to allow this with the `-s` or `--signoff` argument to `git commit` command, providing your `user.name` and `user.email` have been setup correctly.

If you have any questions, you can reach us on Discord