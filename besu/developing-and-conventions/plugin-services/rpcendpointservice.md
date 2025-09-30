# RpcEndpointService

```
public interface RpcEndpointService
extends [BesuService](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html)
```

This service allows you to add functions exposed via RPC endpoints.

This service will be available during the registration callback and must be used during the registration callback. RPC endpoints are configured prior to the start callback and all endpoints connected. No endpoint will actually be called prior to the start callback so initialization unrelated to the callback registration can also be done at that time.

  

## Method Summary

| Modifier and Type | Method | Description |
| --- | --- | --- |
| `<T> void` | `[registerRPCEndpoint](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/RpcEndpointService.html#registerRPCEndpoint(java.lang.String,java.lang.String,java.util.function.Function))​(java.lang.String namespace, java.lang.String functionName, java.util.function.Function<[PluginRpcRequest](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/rpc/PluginRpcRequest.html),​T> function)` | Register a function as an RPC endpoint exposed via JSON-RPC. |

  

## Method Details

- ### [registerRPCEndpoint]
  
<T> void registerRPCEndpoint​(java.lang.String namespace, java.lang.String functionName, java.util.function.Function<[PluginRpcRequest](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/rpc/PluginRpcRequest.html),​T> function) Register a function as an RPC endpoint exposed via JSON-RPC.The mechanism is a Java function that takes a list of Strings and returns any Java object, registered in a specific namespace with a function name.The resulting endpoint is the `namespace` and the `functionName` concatenated with an underscore to create the JSON-RPC method name.The function takes a [`PluginRpcRequest`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/rpc/PluginRpcRequest.html) which contains a list of the inputs expressed entirely as strings. Javascript numbers are converted to strings via their toString method, and complex input objects are not supported.The output is a Java object, primitive, or array that will be inspected via [Jackson databind](https://github.com/FasterXML/jackson-databind). In general if JavaBeans naming patterns are followed those names will be reflected in the returned JSON object. If the method throws an exception the return is an error with an INTERNAL\_ERROR treatment.Type Parameters: T - specified type of return object Parameters: namespace - The namespace of the method, must be alphanumeric. functionName - The name of the function, must be alphanumeric. function - The function itself.