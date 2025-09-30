# BesuContext

  

* * *

```
public interface BesuContext
```

  
Allows plugins to access Besu services.

  

## Method Summary

| Modifier and Type | Method | Description |
| --- | --- | --- |
| `<T extends [BesuService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html)>   java.util.Optional<T>` | `[getService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/BesuContext.html#getService(java.lang.Class))​(java.lang.Class<T> serviceType)` | Get the requested service, if it is available. |

  

## Method Details

- ### [getService]
  
<T extends [BesuService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html)\> java.util.Optional<T> getService​(java.lang.Class<T> serviceType) Get the requested service, if it is available. There are a number of reasons that a service may not be available:
  - The service may not have started yet. Most services are not available before the [`BesuPlugin.start()`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/BesuPlugin.html#start()) method is called
  - The service is not supported by this version of Besu
  - The service may not be applicable to the current configuration. For example some services may only be available when a proof of authority network is in useSince plugins are automatically loaded, unless the user has specifically requested functionality provided by the plugin, no error should be raised if required services are unavailable.Type Parameters: T - the service type Parameters: serviceType - the class defining the requested service. Returns: an optional containing the instance of the requested service, or empty if the service is unavailable