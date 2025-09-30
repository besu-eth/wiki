# Documentation release process

A new stable version of the Besu documentation is released when a new version of the Besu software is released.

> NOTE: If it's the first time (or if any dependencies have changed), you will need to run **`yarn install`** to install Docusaurus
> 
> You will need `node.js` version v18.x (use [NVM](https://nodejs.org/en/download/package-manager#nvm) to easily manage node versions).

To release the documentation, first run the following command to [create a new doc version](https://docs-template.consensys.net/configure/versioning#create-a-docs-version):

```
npm run docusaurus docs:version <VERSION-NUMBER>
```

*(This automatically updates `versions.json`  file to include the new version number.)*

Then, in `docusaurus.config.js` , under `presets > classic > docs`:

- Update the `lastVersion`  to the new version number.

- Under `versions` :
  - Add the new version and set its label to `stable (<VERSION-NUMBER>)` .
  - Update the previous version to remove the `stable`  label.

For example, when updating from version `23.4.1`  to `23.4.2` , update the following section in `docusaurus.config.js`  from the following:

**docusaurus.config.js (before)**

```
lastVersion: "23.4.1",
versions: {
  current: {
    label: "development",
    path: "development",
  },
  "23.4.1": {
    label: "stable (23.4.1)",
  },
  "23.4.0": {
    label: "23.4.0",
  },
},
```

To the following:

**docusaurus.config.js (after)**

```
lastVersion: "23.4.2",
versions: {
  current: {
    label: "development",
    path: "development",
  },
  "23.4.2": {
    label: "stable (23.4.2)",
  },
  "23.4.1": {
    label: "23.4.1",
  },
  "23.4.0": {
    label: "23.4.0",
  },
},
```

commit your changes and push a PR to the besu-docs repo eg [https://github.com/hyperledger/besu-docs/pull/1382](https://github.com/hyperledger/besu-docs/pull/1382) 

When this PR is merged to main, it should trigger a github action which will update [https://besu.hyperledger.org/](https://besu.hyperledger.org/)

The final step is to draft and publish a new release including the changelog on github: [https://github.com/hyperledger/besu-docs/releases](https://github.com/hyperledger/besu-docs/releases)