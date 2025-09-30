# CI/CD Tooling and Process

Besu's CI process is broken into reusable phases, and defers long-running and expensive phases till as late and infrequently as possible, while still ensuring maximum quality checks. CI/CD used to be implemented via CircleCI, but it has since been migrated to Github Actions in an effort to reduce cost as well as be consistent with the majority of Hyperledger projects.

## What this means for users

Users should not notice anything different, other than new delivery urls for Besu releases. [Github Packages and the Github Container Registry](https://github.com/hyperledger/besu/pkgs/container/besu) will be the source for all binaries, but all releases will still be communicated out to users via [Github releases](https://github.com/hyperledger/besu/releases).

## What this means for developers

- As a cost reduction measure (CircleCI for Besu [costs](https://app.circleci.com/insights/gh/hyperledger?branchType=all&projectType=followed&reporting-window=last-30-days) a little under $2K USD per month), long running tests are executed in parallel on low-spec, free action runners. Details on how to run those tests locally are now included in the pull request template, and they can also be manually initiated on the CI/CD infrastructure.
- Releases are now much more fully automated. Any maintainer may create a release from `main`  or a `release-*`  named branch (hereafter referred to as "releasable branches") using standard Github tools.  That process is outlined in more detail below.
- Speed. Breaking up the various workflows into smaller pieces using test splitting results in much greater parallelization, and hence shorter overall runtimes.

## How does it work?

On new PR open, draft or otherwise, the [pre-review](https://github.com/hyperledger/besu/blob/main/.github/workflows/pre-review.yml) workflow is run.

- check for repo compliance via repolinter
- check for source code formatting via spotless
- check gradle tooling validation.
- compile all code
  - then validate javadocs- done later because this depends on bytecode output.
- run unitTests
  - test suites are grouped by gradle subproject, and run in parallel
  - any test failures will be annotated on the PR.

Overall this looks like:

![](./attachments/Screenshot%202024-01-18%20at%201.57.16%E2%80%AFPM.png)

  

It takes about 15 minutes, end to end, but if we can be smarter about splitting the unit tests we could easily cut that in half. 

At the same time, other workflows execute the more expensive test suites before allowing a merge to a releasable branch.

- run integrationTests
- run acceptanceTests
- run referenceTests

Test results can then be annotaed directly on to the PR, and any failures would prevent merging into main.  You'll also find junit test result artifacts attached to the workflow run, and a summary of how each test shard performed. 

## Common Patterns

There are a couple of common patterns worth explaining in this pipeline. We regularly need to determine if a long-running test suite should run, how to split up tests, and how to consolidate results.

- test splitting is handled by a github action which intends to group them by the most even runtime based on past runs. In the case of the EVM reference tests, the sheer volume seemed to overwhelm it. Those tests are split up using a simple bash script.
- testing workflows that use a matrix strategy for parallelization, will also have a consolidating job that waits for them all to complete, before marking the workflow run as passed.

## Merging to Main

We now can rely on a branch [ruleset](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets) to collect all our rules about merging to a releasable branch.  Merging to `main` or any `release-*` named branch is denied until:

- pre-review checks have passed on the merge result, and the PR has a `unittests-passed`  status.
- PR has an approval from at least one project maintainer.
- acceptance test checks have passed on the merge result, and the PR has an `accepttests-passed` status.
- integration test checks have passed on the merge result, and the PR has an `integration-tests` status. This one is named differently because it does not need a consolidating job, as described above.
- reference test checks have passed on the merge result, and the PR has a `reftests-passed` status.

Once all these are confirmed, the PR may be merged, and all statuses should be transferred to the corresponding commit on the target branch. That commit would now be considered releasable. 

## Release Process

This process supports (and encourages) releasing directly from main, but also allows for the creation of release specific branches for hotfixes or interim releases which must not include what is currently on main.

When a github release is created (pre-release or otherwise) then the following artifacts are built, and attached to the release:

- tarball - release version embedded in the file name.  The release description has the sha256 sum for this file appended to it.
- zipfile - release version embedded in the file name.  The release description has the sha256 sum for this file appended to it.
- docker images created and tagged.
- if a non-pre-release is published, the `latest`  tag is moved to the release image.

All artifacts will have the version number specified in the created github release, no modification to source is necessary, and so none of the testing above needs to be re-executed.

Example release [can be seen here](https://github.com/jflo/besu/releases/tag/24.1.0-RCD).

## Emergency Takedown Process

On the discovery of a known bad release, build artifacts can be removed from circulation.

- Do not delete the release in github, rather update it to explain it was found to be faulty.
- Be sure to include what alternate version(s) to use instead.
- When editing the release, delete the attached build artifacts.
- Do not remove the file hashes from the release notes, rather mark them up as strikethrough so they are still available, but discouraged.
- Delete the docker images from the package management screens, for all image variants.
- Communicate on social media if necessary.

This process was tested during initial implementation of this CI/CD pipeline, and [an example can be found here](https://github.com/hyperledger/besu/releases/tag/24.2.0-RC1).

## Developer Notes

In addition to the rulset defined above, there is another important repository setting that needs to be actively maintained: [Actions Permissions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository#allowing-select-actions-and-reusable-workflows-to-run). When a new github action is to be used, or an existing one updated, it must be referenced by the specific git sha for that release. This prevents any tags that may be moved on the action distribution from causing a change in what actions are run.