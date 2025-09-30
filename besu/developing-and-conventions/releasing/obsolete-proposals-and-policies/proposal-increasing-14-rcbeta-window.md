# Proposal: Increasing 1.4 RC/Beta window

**Summary:** Increase the "beta/RC" window for 1.4 by one to two releases to the left to facilitate testing a large scale change

**Background**

We have a fairly large scale change under review ([besu#215](https://github.com/hyperledger/besu/pull/215)) that is taking our internal BytesValue values that wrap byte arrays and replacing it with an crypto focused Apache library that does the same handling.  This is a very large (10K+) change and very far reaching.

1. One maintainer raised the point that with such a large change how are we sure that the test cover everything and are stable and performant?  
In addition to existing unit tests, integration tests, acceptance tests, and reference tests we may want to spend more time just running nodes.  
  
2. This change also opens up the possibility of adding rich byte handling to our plugins API instead of simply passing byte arrays.  
  1. This cannot be done in a bi-weekly release because it is a breaking change
  2. We need to co-ordinate with the authors of all the plugin APIs to validate if this change is good for the particular plugin
  3. This may reduce friction between the plugins API and the core of Besu 

  

**Proposals:**

- Beta Releases
  - Stop releasing 1.3 releases in December (1.3.7) except for important bug fixes
    - a new 1.3 branch is made if we need fixes
  - Release two 1.4-beta releases in January,
    - this takes over the "master" branch
  - Release the RC in early February (current schedule)
  - Release the 1.4 in late February (current schedule).
  - Ship the Tuweni PR as the first commit after we stop 1.3 support
  - Including Plugin API changes
- Longer RC Cycle
  - Stop releasing 1.3 releases after first January release (1.3.8) except for important bug fixes
    - a new 1.3 branch is made if we need fixes
  - Release 1.4 RC in mid January (2 weeks earlier)
  - Release more RCs as warranted
  - Release the 1.4 in late February (current schedule).
  - Ship the Tuweni PR as the first commit after we stop 1.3 support
  - Including Plugin API changes
- Status Quo
  - No schedule changes
  - Ship the Tuweni PR when it is ready with all others in a bi-weekly release
  - Maybe do plugin API changes as part of the 1.4 release

The down side of the status quo approach is that it provides a very limited window to co-ordinate the use of the plugin APIs by downstream consumers, about 2 weeks or less.  By going with one of the longer cycles there is more co-ordinating time.  Going with a "beta" release would imply that things may change in response to testing.  However going with a longer RC window reduces the amount of time we are off of bi-weekly agile releases.