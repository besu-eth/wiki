# Using Postman with Besu

### Interacting With a Besu Node in Postman (JSON-RPC API)

- The Besu Private Network Quickstart makes use of cURL, however JSON-RPC requests can also be made in Postman. [https://besu.hyperledger.org/en/1.3.0/Tutorials/Quickstarts/Private-Network-Quickstart/#run-json-rpc-requests](https://besu.hyperledger.org/en/1.3.0/Tutorials/Quickstarts/Private-Network-Quickstart/#run-json-rpc-requests)
  - Create a Postman account with your ConsenSys email, and then download and install Postman on your device. [https://www.postman.com/downloads/](https://www.postman.com/downloads/)
  - Sign into the Postman desktop application. On the menu bar, click on Workspaces and select ‘Create Workspace’. Give the workspace a relevant name and summary, then set the visibility to ‘Personal’.
  - Within your workspace, you can import the Besu RPC collection by clicking on Import and selecting ‘Link’. Paste the following address and select Import: [https://besu.hyperledger.org/en/stable/postman/postman\_collection.json](https://besu.hyperledger.org/en/stable/postman/postman_collection.json)
  - Create a new environment by clicking on the eye symbol on the upper right hand side of Postman, then select ‘Add' on the same line as Environment. Use the image below as a guide to create three variables with the current values shown. The http port for Besu is 8545 by default, so if you are running it on a different port, be sure to modify the rpc-http-port and jsonrpc.endpoint values to match that.
  - Then click the three dots icon next to ‘Share’ and select ‘Set as active environment’. If you already have a Besu node that is mining running, you can try sending an eth\_mining call, of which the result should be true.