# How to Contribute-

# Contents

- [Things to be Aware of before Contributing](#things-to-be-aware-of-before-contributing)
  - [The Developer Certificate of Origin (DCO) checks](#the-developer-certificate-of-origin-dco-checks)
  - [Copyright and License](#copyright-and-license)
- [Contributing Code or Documentation](#contributing-code-or-documentation)
- [How to work with DCO](#how-to-work-with-dco)
  - [When Committing](#when-committing)
  - [When Merging](#when-merging)
  - [When you have a DCO failure on your PR from DCO Bot](#when-you-have-a-dco-failure-on-your-pr-from-dco-bot)
  - [When you have a DCO failure on your PR from CI](#when-you-have-a-dco-failure-on-your-pr-from-ci)
- [Becoming a Maintainer](#becoming-a-maintainer)

# Things to be Aware of before Contributing

Be sure to read the [contribution guidelines](https://github.com/hyperledger/besu/blob/master/CONTRIBUTING.md) for more details on searching and creating issues.

## The Developer Certificate of Origin (DCO) checks

As per section 13.a of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all code submitted to the Hyperledger Foundation needs to have a [Developer Certificate of Origin](http://developercertificate.org/) (DCO) sign-off.

This certifies that you are able to submit your contribution to our repository under the license of the repository, and for the contribution to be redistributed under that same license.

You can "sign" this certificate by including a line in the git commit of "`Signed-off-by: Legal Name <email-address>`".

## Copyright and License

As per section 13.a of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all new code submitted to the Hyperledger Foundation needs to be under the Apache License, Version 2.0.

As per section 13.c of the [Hyperledger Charter](https://www.hyperledger.org/about/charter) all new documentation submitted to the Hyperledger Foundation needs to be under the Creative Commons Attribution 4.0 International License.  

You may maintain copyright to your works under these two clauses.

When you commit code please ensure you:

- put your copyright if required
- you MUST put the SPDX license header using Apache 2.0 like below. If you do not put the header in the build will fail the license header check

```
 /* SPDX-License-Identifier: Apache-2.0 */
```

  

# Contributing Code or Documentation

The codebase and documentation are maintained using the same "*contributor workflow*" where everyone without exception contributes changes proposals using "*pull-requests*".

This facilitates social contribution, easy testing, and peer review.

To contribute changes, use the following workflow:

1. [Fork the repository](https://github.com/PegaSysEng/besu/fork).
2. **Clone your fork** to your computer.
3. **Create a topic branch** and name it appropriately.  Starting the branch name with the issue number is a good practice and a reminder to fix only one issue in a Pull-Request (PR).
4. **Make your changes** adhering to the coding conventions described in the associated repository's `CONTRIBUTING.md`  file.  *In general a commit serves a single purpose and diffs should be easily comprehensible.  For this reason do not mix any formatting fixes or code moves with actual code changes.*
5. **Commit your changes** see [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/) article by Chris Beams and ensure there is a `Signed-off-by: Legal Name <email-address>` line in the commit to submit the code under a [Developer Certificate of Origin (DCO)](http://developercertificate.org/).
6. **Test your changes** locally before pushing to ensure that what you are proposing is not breaking another part of the software. Running the `./gradlew clean check test`  command locally will help you to be confident that your changes will pass CI tests once pushed as a Pull Request.
7. **Push your changes** to your remote fork (usually labeled as `origin`).
8. **Create a pull-request** (PR) on the Besu repository. If the PR addresses an existing Jira issue,  include the issue number in the PR title in square brackets (for example,`[PAN-2374]`).
9. **Add labels** to identify the type of your PR. *For example, if your PR is not ready to validate, add the "work-in-progress" label. If it fixes a bug, add the "bug" label.* If the PR address an existing Jira issue, comment in the Jira issue with the PR number.
10. **Ensure your changes are reviewed**. *Select the reviewers you would like to review your PR. If you don't know who to choose, simply select the reviewers proposed by GitHub or leave blank.*
11. **Make any required changes** on your contribution from the reviewers feedback.  *Make the changes, commit to your branch, and push to your remote fork.*
12. **When your PR is validated**, all tests passed and your branch has no conflicts with the target branch, you can **"squash and merge"** your PR, when doing so ensure that there is a `Signed-off-by: Legal Name <email-address>` line in the commit message to comply with [DCO](http://developercertificate.org/)  and you're done. You contributed to Besu! Thanks !

# How to work with DCO

## When Committing

You need to ensure that every commit message has a line "`Signed-off-by: Your Legal Name <your-email@address>`", and while you could add that manually every time, here are the steps to follow so the computer can add it for you:

1. Set your legal name in the git configuration:  
`git config user.name "Legal Name"` 
2. Set your email in the git configuration:  
`git config user.email "email@address"` 
3. Add the `-s`  or `--signoff`  to all `git commit`  invocations.
  1. Add a git alias:  
`git config --global alias.c 'commit --signoff'   `and then run "`git c`" instead of "`git commit`"
  2. In IntelliJ  
![](./attachments/Screen%20Shot%202019-09-17%20at%2010.13.13%20am.png)

## When Merging

The merge or a PR must also have a DCO so we can know the entire repository is under the associated license.

1. When Merging a Pull Request through **"squash and merge"**, include the `Signed-off-by` lines from every contributor, and add one for you as the person merging.

## When you have a DCO failure on your PR from DCO Bot

![](./attachments/Screen%20Shot%202019-09-17%20at%208.27.56%20am.png)

'

Click on that "Details" link and follow the instructions.

![](./attachments/Screen%20Shot%202019-09-17%20at%208.28.18%20am.png)

## When you have a DCO failure on your PR from CI

On Circle CI you will see:

![](./attachments/Screen%20Shot%202019-09-17%20at%2012.35.45%20pm.png)

On Jenkins in the full Console Output you will see:

![](./attachments/Screen%20Shot%202019-09-17%20at%2012.39.47%20pm.png)

If this is only from CI and not from DCO Bot, then please contact a Maintainer, as it probably means that the `master` branch has a commit that does not follow DCO which will necessitate a `master` rebase.

# Becoming a Maintainer

Besu welcomes community contributions and encourages diversity in its maintainers. To become a maintainer, please read the [maintainers](https://github.com/hyperledger/besu/blob/master/MAINTAINERS.md) document in the repo before seeking sponsorship.