# PermissioningService

```
public interface PermissioningService
extends [BesuService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html)
```

This service allows plugins to decide who you should connect to and what you should send them.

Currently, there are two hooks available; connection permissioning and message permissioning.

- **Connection permissioning** - checks if inbound and outbound connections to peers are permitted. [`NodeConnectionPermissioningProvider`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeConnectionPermissioningProvider.html)
- **Message permissioning** - checks if a devp2p message can be sent to a peer. [`NodeMessagePermissioningProvider`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeMessagePermissioningProvider.html)

  

## Method Summary

| Modifier and Type | Method | Description |
| --- | --- | --- |
| `void` | `[registerNodeMessagePermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PermissioningService.html#registerNodeMessagePermissioningProvider(org.hyperledger.besu.plugin.services.permissioning.NodeMessagePermissioningProvider))​([NodeMessagePermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeMessagePermissioningProvider.html) provider)` | Registers a callback to allow the interception of a devp2p message sending request |
| `void` | `[registerNodePermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PermissioningService.html#registerNodePermissioningProvider(org.hyperledger.besu.plugin.services.permissioning.NodeConnectionPermissioningProvider))​([NodeConnectionPermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeConnectionPermissioningProvider.html) provider)` | Registers a callback to allow the interception of a peer connection request |

  

## Method Details

- ### [registerNodePermissioningProvider]
  
void registerNodePermissioningProvider​([NodeConnectionPermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeConnectionPermissioningProvider.html) provider)  
Registers a callback to allow the interception of a peer connection requestParameters: provider - The provider to register
- ### [registerNodeMessagePermissioningProvider]
  
void registerNodeMessagePermissioningProvider​([NodeMessagePermissioningProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/permissioning/NodeMessagePermissioningProvider.html) provider)  
Registers a callback to allow the interception of a devp2p message sending requestParameters: provider - The provider to register