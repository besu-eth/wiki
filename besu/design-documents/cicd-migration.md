# CI/CD Migration

Moving from CircleCI to GitHub Actions (GHA)

TBD:  HL to provide background on the motive and strategy

## GHA Impressions

Porting over the functionality from CircleCI was tedious, but fairly straightforward. Current progress can be seen [in this fork](https://github.com/jflo/besu/actions). The design of small components combined with access to the runners via self-hosting (seldom necessary), made the development process pretty accessible. Being able to tie into the GitHub event stream allows for improved and [simplified release processes that can be adopted incrementally](https://github.com/hyperledger/besu/pull/4791).

Secrets management was simple and straightforward. Secrets are defined in the repo settings, and are injected for use by the action definition. Logging output was properly obfuscated whenever a secret was used.  

Minimal changes were required to Gradle based build tasks, though the delegation to gradle for publishing and tagging complicates things.  Suggest removing those concerns from gradle. It makes sense for gradle to know how to produce artifacts like tarballs and docker images, but release related metadata should be managed externally.

The use of self-hosted runners should likely be avoided due to cost and [security concerns](https://johnstawinski.com/2024/01/11/playing-with-fire-how-we-executed-a-critical-supply-chain-attack-on-pytorch/).

## Challenges

File Permissions: File ownership and permissions get pretty convoluted when using any docker based action. Since they have no notion of the UID to run as, their output ends up being owned by root. [This action](https://github.com/marketplace/actions/reset-workspace-ownership-action) was used to work around the problem, and it can be avoided all together by using Github hosted runners instead of self-hosted ones.

Test Splitting: A large portion of the time spent was to re-implement test splitting so many hosts can all run the tests in parallel. This is a feature supported by CircleCI, but the only GHA support for this function to be found is [still in alpha](https://github.com/marketplace/actions/split-tests). We are currently only dividing the number of tests evenly across runners, however there is another means of test splitting that warrants investigation: one based on the test timings available via a previous runs junit results.

Cost: While an in-depth cost analysis has not been done yet, suspect it will be nearly free.  Full CI/CD pipeline was runnable on free tier Github hosted runners.

## Planned CI/CD Design

Subdivide CI process into reusable phases, and defer long-running and expensive phases till as late and infrequently as possible, while still ensuring maximum potential quality checks.

On new PR open, draft or otherwise, the following actions would happen.

- check for repo compliance via repolinter
- check for source code formatting via spotless
- check gradle tooling validation.
- compile all code
  - then validate javadocs- this depends on bytecode output.
- run unitTests
  - any test failures will be annotated on the PR.
  - tests will be sharded to run in parallel.

This is referred to as the pre-review workflow, feel free to [take a look at it in this fork](https://github.com/jflo/besu/actions/runs/7560587947), but overall it looks like this:

![](./attachments/Screenshot%202024-01-18%20at%201.57.16%E2%80%AFPM.png)

  

It takes about 20 minutes, end to end, but if we can be smarter about splitting the unit tests we could easily cut that in half. 

Once the PR is approved, the following can be run in parallel.

- run integrationTests
- run acceptanceTests
- run referenceTests

Test results can then be posted back to the PR, and any failures would prevent merging into main.  [You'll notice](https://github.com/jflo/besu/actions/runs/7494062506) that the acceptanceTest phase no longer requires us to separate out private network tests.  We divide all these tests across 16 runners in parallel, and it completes in 17 minutes. You'll also find test results attached to the workflow run, and a summary of how each test shard performed. This is also the case for integration and reference tests as well.

## Merging to Main

Merging to `main` or any `release-*` named branch should be denied until:

- pre-review checks have passed on the merge result, and the PR has a `pre-review`  status.
- PR has an approval from at least one project maintainer.
- acceptance test checks have passed on the merge result, and the PR has an `acceptance-tests` status.
- integration test checks have passed on the merge result, and the PR has an `integration-tests` status.
- reference test checks have passed on the merge result, and the PR has a `reference-tests` status.

Once all these are confirmed, the PR may be merged, and all statuses should be transferred to the corresponding commit on the target branch. That commit would now be considered releasable. 

  

## Planned Release Process Design

Current release process supports (and encourages) releasing directly from main, but does allow for the creation of release specific branches for hotfixes or interim releases which must not include what is currently on main.

When a github release is created (pre-release or otherwise) then the following artifacts are built, and attached to the release:

- tarball - release description has the sha256 sum for this file appended to it.
- zipfile - release description has the sha256 sum for this file appended to it.
- docker images created and tagged.

All artifacts will have the version number specified in the created github release.

Example release [can be seen here](https://github.com/jflo/besu/releases/tag/24.1.0-RCD).

  

## Outstanding issues, Suggested improvements

1. Since we can now execute a release fully from Github, we need to secure and establish policy around how releases are created.
2. HL has expressed an interest in using Github Packages for the storage and distribution of artifacts. This has not been implemented yet but poses no technical challenge.
3. Building multi-arch docker images without requiring an arm based self-hosted runner.
4. More optimal splitting of tests based on prior runtimes.
5. Factoring out of tagging/version numbering. Things are way easier when we force the version number to be used to always be provided.
6. TODO: Tivy scans/tests are not implemented yet
7. TODO: Java jar publication to artifactory. Holding for feedback from users who require maven artifact resolution.
8. TODO: how to recover stdout from various tests