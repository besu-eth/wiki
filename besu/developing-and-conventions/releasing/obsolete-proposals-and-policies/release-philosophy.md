# Release Philosophy

The general philosophy behind Besu release numbering is as follows.

We bump the milestone when a release is big enough (such as full Mainnet compliance).

We do a quarterly release where we upgrade all dependencies with a RC release.

Feature development is done on the main branch in GitHub. Significant features should include a [feature flag](../../../../besu/design-documents/feature-flags.md) so that the feature can be disabled by default.

We don’t do feature branches.

We do patch releases on a fortnightly cadence to allow access to bug fixes without delay.

  

As for numbering itself, the following approach is used:

- "Major Version" means a version of the Software identified by a change in the digit to the left of the left-most decimal point (X.x.x).
- "Minor Version" means a version of the Software identified by a change in the middle number in between the two decimal points (x.X.x).
- "Maintenance Version" means a version of the Software identified by a change in the digit to the right of the rightmost decimal point (x.x.X).
- We are not using semantic versioning.