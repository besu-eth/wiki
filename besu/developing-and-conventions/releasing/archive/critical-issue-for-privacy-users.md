# Critical Issue for Privacy Users

**Note:** If your network does not have any private transactions created using Hyperledger Besu 1.3.4 or earlier, you are not affected by this issue.

Between version 1.3.4 and 1.3.5 there was a change in the way that the private database metadata was maintained. Unfortunately, users upgrading from 1.3.4 or earlier to 1.3.5 or later with existing private transactions in their chain will lose any private transaction execution data for private transactions created using 1.3.4 or earlier. The execution data is created when executing the private transaction and includes logs, output, status, and revert reason. The execution data is not the private transaction itself and can be recreated by re-executing the private transaction.  

No public or private transactions are lost. The public chain still contains all the privacy marker transactions and Orion still contains all the private transaction payloads so resynchronising your Besu node from other peers recreates the private transaction execution data.  
  
To recover:  
1\. Start a new Hyperledger Besu node running  v1.3.5 or higher (preferably 1.4.0 or higher) using the same Orion nodes.  
2\. Resync the chain from another Hyperledger Besu node.

As always, the PegaSys team is happy to answer any questions or help you with any issue you may have.  Contact us on RocketChat!