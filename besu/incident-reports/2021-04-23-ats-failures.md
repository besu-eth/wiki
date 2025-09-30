# 2021-04-23 ATs failures

**Context**: AT’s started failing late April 2021

- This Circle CI report is interesting - significant failures vs successes
- these failures started happening April 23

coinciding with (but not known to be caused by) the introduction of PRs:

- SECP256R1 (PR 2008)
- container tests (Tessera in Orion mode; some Besu privacy ATs)
  - notably, the Tessera in Orion mode container tests did not get merged into master
  - also I think the Besu container tests step has been disabled?

This appears to be a problem with the Vertex queue being blocked and this likely happens because:

- running out of entropy
- code changes
- init ing too often

  

Investigate:

**Entropy:**

- confirm what the entropy is during the tests . Run the following during the tests and see how low it dips. If this dips below 1k, then this isn't good. If the entropy is fine during and at the end of the tests runs, entropy isn't the problem
```
watch -n 2 cat /proc/sys/kernel/random/entropy_avail
```
- The ATs have an override file [https://github.com/hyperledger/besu/commit/dac36a5665e0fb574eca8c814881f60ef087ae49](https://github.com/hyperledger/besu/commit/dac36a5665e0fb574eca8c814881f60ef087ae49)Confirm that the native libs are NOT using this. If so how can they be set to respect these settings? If they are reading from java.security then amend that file or provide an override( preferable, but better still is to get it to respect the AT settings directly)
- **If** entropy is the problem look to seed a device and use that - use haveged etc

What have we tried:

- reducing parallelism - was 8, changed to 6 → AT time 12 min → 15 min
- installing haveged on AT executor → seemed to be better
- explicitly setting securerandom.source=/dev/urandom → no change evident
- removing haveged and explicitly setting securerandom.source=[file:/dev/urandom](http://file/dev/urandom) → ATs failed in 8 min with a ECDH “Invalid point coordinates” error. NO “blocked thread” errors in logs.
- explicitly setting securerandom.source=[file:/dev/./urandom](http://file/dev/./urandom) → same behaviour as [file:/dev/urandom](http://file/dev/urandom)
- installing haveged and explicitly setting securerandom.source=[file:/dev/urandom](http://file/dev/urandom) → ATs pass in 8 min.
- **so the PR that failed on SECP invalid point coordinates didn't have haveged. With haveged, and securerandom.source=[file:/dev/urandom](http://file/dev/urandom) this PR has passed 2 times with ATs ~ 8 min. reference tests now take longer!**  
Third run failed (but no exceptions in the logs)

**Code Changes:**

- what was the last good commit where tests were fine?
  - Looking at PRs merged into master, [2181](https://github.com/hyperledger/besu/pull/2181) was merged 22/23 April and [2008](https://github.com/hyperledger/besu/pull/2008) was merged 21/22 April
- 2008 introduced SECP256R1 ie a new signature algorithm. Which generates a different public key from the same private key. And the reference to the signature algorithm is static in KeyPairUtil. So if those tests run first then other tests fail because the wrong signature algo is being used. So [https://github.com/hyperledger/besu/pull/2273](https://github.com/hyperledger/besu/pull/2273) ignores these tests. for now.
- what new code/features were introduced?

**The answer**

Three things

- install haveged on AT executor.
- set the property securerandom.source=[file:/dev/urandom](http://file/dev/urandom) explicitly for ATs
- [disable](https://github.com/hyperledger/besu/pull/2273) ATs for SECP256R1 because there is a static reference to the signature algorithm in KeyPairUtil so this needs some refactoring to handle multiple algos