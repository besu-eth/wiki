# Release Process

### Principles and Benefits

- main should always be release-able
- a chain of commits in the release branch from main provide provenance of a release
- the ability to merge PRs into main is uninhibited by the release process, and the release process itself is not encumbered by changes to main
- the RC process provides a crisp delineation of burn-in build artifacts and final release artifacts
- cherry-picking commits to compose a release remains possible, if discouraged

### Example Release Workflow for a hypothetical HL Besu 24.7.3

#### Burn-in candidate release steps (Day 0)

1. Create a PR against main to add a new version section to [CHANGELOG.md](http://CHANGELOG.md) to reflect the next snapshot revision
  1. This prevents blocking main during the release but creates a bookmark to indicate that the release will include up to the commit before this.
2. Create a release candidate PR which merges \`main\` as of the release point into the \`release-<version>\` branch.
3. When release branch exists and is tagged, any pre-release activities may commence. This usually includes executing a long-running (about 48 hours) "burn in" process which deploys new nodes to sync from scratch on a variety of networks, using a variety of CL clients.
4. At this point, there is no published artifact, and testing may take as long as deemed necessary.

#### Final release steps (Day X)

Upon successful validation of the release candidate burn-in:

1. Define a new release on GitHub using the <version> for the release.
  1. draft a new github release for <version>
  2. publish the github release and announce on HL discord. This will create a new release and all artifacts will be versioned based on the string in the name of the release.
  3. build artifacts will be attached to the release, and accurate SHAs and docker locations will be amended.
2. Trigger release process for documentation - [Documentation release process](../../../besu/documentation/documentation-archive/documentation-release-process.md)
3. Homebrew release

#### Burn-in failures and hotfixes

An alternate outcome where the burn-in fails is a no-op.  Nothing needs to happen to 'cancel the release'.   We can either skip this release version (and note that outcome in CHANGELOG.md), or build an RC2 candidate by restarting the burn-in candidate steps at step #2 with the new RC number.  

This process leaves a cherry-pick escape hatch for hotfixes that is minimum friction for the latest release at least. The biggest element of friction here is the PR which merges main into the release would need to handle the merge conflict that a cherry-pick creates.  This implies that it would be desirable for cherry-picking should to be a rare event, that is done with care. 

  

Comments, feedback, and clarification are all welcome.