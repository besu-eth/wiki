# Using CalVer for Besu Releases

On 17 Sep 2020 the Hyperledger TSC voted to [Allow projects to use CalVer or SemVer](https://lf-hyperledger.atlassian.net/wiki/display/TSC/Allow+projects+to+use+CalVer+or+SemVer).  

General background on Calendar Versioning (CalVer) - [https://calver.org/](https://calver.org/)

## CalVer taxonomy: YY.M.patch

- YY: Year (20, 21, 22, etc.)  
- M: Month (1, 2, 3, ..., 11, 12). 
- Patch: Fortnightly releases, or whenever sub-month releases happen.
- YY.M.patch: The year and month are from the current month.

## Breaking Changes Policy

- No intentional backwards incompatible breaking changes should occur without 3 months of prior notice via the deprecation policy.
  - Java Plugin APIs
  - CLI flags and configuration files
  - On-disk storage compatibility
  - JSON-RPC APIs
- Patches may introduce forwards compatible changes, such as (but not limited to) new features, new fork or chain support, and new JSON-RPC apis.
- A notice for an intentional breaking change should be in the CHANGELOG.md file for at least 3 months. 
- Examples of such changes:
  - Changing the required JDK.  (such as when we went form Java 17 to Java 21).
  - Removing storage formats, or required migrations.
  - Dropping obsolete CLI flags, such as the whitelist series flags (replaced by the allowlist series)
- This breaking change policy will not prohibit rapid release of security related updates.