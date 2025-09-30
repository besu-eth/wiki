# Versioned documentation

Every Besu documentation version is [tagged in the repository](https://github.com/hyperledger/besu-docs/releases), but the published documentation site only contains the in-flight latest version – that is, new documentation is published as features are released.

## Document version-specific information

We recommend most users upgrade to the latest version of Besu (especially on Mainnet), but for some enterprise use cases, it might be helpful to include version-specific information in the documentation. For example, if a new JSON-RPC method `qbft_getPendingVotes`  is released with version 24.9.0, add something like the following to the method description. This informs enterprise users whether their version of Besu supports the new method.

![](./attachments/Screenshot%202024-09-24%20at%2011.15.05%E2%80%AFAM.png)

## View older documentation versions

To build or host a specific older version of the documentation (for example, 23.7.1):

1. Clone the `besu-docs` repository and checkout the tag for your intended version:
  - `git clone git@github.com:hyperledger/besu-docs.git`
  - `cd besu-docs`
  - `git checkout 23.7.1`
2. Build and run locally:
  - `yarn`
  - `yarn run start`
3. Open a browser tab and navigate to `[http://localhost:3000/development](http://localhost:3000/development)`
4. (Optional) Host this version on your own infrastructure (for example, nginx or s3):
  - `yarn`
  - `yarn run build`
  - `yarn run serve` (optional – this is to check the output locally) 

          Host the contents of the `build` folder on your own infrastructure.