# Feature Flags

## Feature Flags

## Feature Overview(2-3 sentences): 

All significant new features should have a feature flag of some sort that can disable the feature.  Acceptable flags are genesis file configurations and cli flags.  A centralized feature flag file will be shared for command line flags

## Rationale

Usually major features added tot he Ethereum chain are tied to various hard forks, such as Berlin, Phoenix, and Istanbul.  There are other features that are not tied to hard forks that can impact system stability and usability, such as devp2p upgrades and use of native libraries.  While a hard fork can be disabled via configuration other major features cannot be.  To keep the codebase stable these new features should be disabled for at least one quarterly release, defaulting to off on their first release, on when deemed stable, and when it has been defaulted on between two quarterly releases the flag should be removed.

## Potential Risks / Rabbit Holes: 

- We could feature flag too much stuff, we need to exercise judgement in what gets flagged.

## Out of scope:

- testing all possible feature flag combinations.  The current default set and individual features should still get coverage in acceptance and unit tests.

## Longer description: 

### What does *not*  get feature flagged?

- Network Hard Forks where the fork is known and stable.   
(these are already flagged by the genesis config)
- Features that are meant to be turned on and off via CLI  
Example: GraphQL.  The flag to turn it on is already a feature flag.
- Every little bug.  What gets flagged needs to be big enough to be called a feature

### What *must* get a feature flag?

- New devp2p sub protocols such as ETH/64 and Eth/65
- Changing existing code to non-java implementations via JNI, such as secp256k1 encryption.
- Speculative EIPs, such as EIP-1559 or eWASM, that may show up in future forks.

### Feature Flag file

To support this a new feature flag file will be added into the \`:config\` project.

- Fields and methods will be static
- Access will be via getters

BesuCommand will responsible for setting the the values from CLI flags

- Flags names will be of the form \`--X<foo>-enabled\`
- Setting via BesuCommand may be enforced in future releases via error prone
- Future releases may make the setting the flags only accessible to BesuCommand via Java 9 module system