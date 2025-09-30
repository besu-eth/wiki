# PrivacyPluginService

```
public interface PrivacyPluginService
extends [BesuService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html)
```

  
A service that plugins can use to define how private transactions should be handled.  
  
You must register a [`PrivacyPluginPayloadProvider`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyPluginPayloadProvider.html) when using this plugin and can optionally register a [`PrivateMarkerTransactionFactory`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivateMarkerTransactionFactory.html) and a [`PrivacyGroupGenesisProvider`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupGenesisProvider.html)

  

## Method Summar

| Modifier and Type | Method | Description |
| --- | --- | --- |
| `[PrivacyPluginPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyPluginPayloadProvider.html)` | `[getPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#getPayloadProvider())()` |     |
| `[PrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupAuthProvider.html)` | `[getPrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#getPrivacyGroupAuthProvider())()` |     |
| `[PrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupGenesisProvider.html)` | `[getPrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#getPrivacyGroupGenesisProvider())()` |     |
| `[PrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivateMarkerTransactionFactory.html)` | `[getPrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#getPrivateMarkerTransactionFactory())()` |     |
| `void` | `[setPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#setPayloadProvider(org.hyperledger.besu.plugin.services.privacy.PrivacyPluginPayloadProvider))​([PrivacyPluginPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyPluginPayloadProvider.html) privacyPluginPayloadProvider)` | Register a provider to use when handling privacy marker transactions. |
| `void` | `[setPrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#setPrivacyGroupAuthProvider(org.hyperledger.besu.plugin.services.privacy.PrivacyGroupAuthProvider))​([PrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupAuthProvider.html) privacyGroupAuthProvider)` | Register a provider to use when auth requests for a multi-tenant environment. |
| `void` | `[setPrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#setPrivacyGroupGenesisProvider(org.hyperledger.besu.plugin.services.privacy.PrivacyGroupGenesisProvider))​([PrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupGenesisProvider.html) privacyGroupAuthProvider)` | Register a provider for initialising private state genesis |
| `void` | `[setPrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/PrivacyPluginService.html#setPrivateMarkerTransactionFactory(org.hyperledger.besu.plugin.services.privacy.PrivateMarkerTransactionFactory))​([PrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivateMarkerTransactionFactory.html) privateMarkerTransactionFactory)` | Register a factory to specify your own method for signing and serializing privacy marker transactions. |

  

## Method Details

- ### [setPayloadProvider]
  
void setPayloadProvider​([PrivacyPluginPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyPluginPayloadProvider.html) privacyPluginPayloadProvider)  
Register a provider to use when handling privacy marker transactions.Parameters: privacyPluginPayloadProvider - the provider to use for the privacy marker payload
- ### [getPayloadProvider]
  
[PrivacyPluginPayloadProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyPluginPayloadProvider.html) getPayloadProvider()
- ### [setPrivateMarkerTransactionFactory]
  
void setPrivateMarkerTransactionFactory​([PrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivateMarkerTransactionFactory.html) privateMarkerTransactionFactory)  
Register a factory to specify your own method for signing and serializing privacy marker transactions.Parameters: privateMarkerTransactionFactory - the factory to use to build the privacy marker transaction
- ### [getPrivateMarkerTransactionFactory]
  
[PrivateMarkerTransactionFactory](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivateMarkerTransactionFactory.html) getPrivateMarkerTransactionFactory()
- ### [setPrivacyGroupAuthProvider]
  
void setPrivacyGroupAuthProvider​([PrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupAuthProvider.html) privacyGroupAuthProvider)  
Register a provider to use when auth requests for a multi-tenant environment. If you are not using a multi-tenant environment you always return true.Parameters: privacyGroupAuthProvider - the provider to use to determine authz
- ### [getPrivacyGroupAuthProvider]
  
[PrivacyGroupAuthProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupAuthProvider.html) getPrivacyGroupAuthProvider()
- ### [setPrivacyGroupGenesisProvider]
  
void setPrivacyGroupGenesisProvider​([PrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupGenesisProvider.html) privacyGroupAuthProvider)  
Register a provider for initialising private state genesisParameters: privacyGroupAuthProvider - the provider for the initial private state
- ### [getPrivacyGroupGenesisProvider]
  
[PrivacyGroupGenesisProvider](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/privacy/PrivacyGroupGenesisProvider.html) getPrivacyGroupGenesisProvider()