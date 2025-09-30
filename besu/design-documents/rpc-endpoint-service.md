# RPC Endpoint Service

# Summary

Add a new service for the Plugins API where new RPC endpoints can be registered and handled.

# Motivation

End users may want to expose custom RPC services as part of the existing RPC services instead of creating their own endpoint.  These may reflect existing data in interesting ways (perhaps a specific smart contract).  Or they may be used by other plugins to provide administrative APIs to do such things as adjust their configuration on the fly.

Plugins can still start their own network endpoint if the existing JSON-RPC and WebSockets facilities fail to meet their needs.

# Design

1. Add a new RPCEndpointService to the standard services exposed by the plugin framework.
  1. This service has one method to register a JSON-RPC endpoint with three parameters  
  
namespace - the part of the JSON-RPC method before the underscore, this string must only be alphanumeric  
functionName - the part of the JSON-RPC method after the underscore, this string must only be alphanumeric.  
function - a method reference that takes in a RPC call object and returns an object.  This object must be JavaBeans parsable as it will be JSON serialized based on the getters.  
  
  2. The RPC call object will initially contain only a list of strings corresponding to the positional parameters of the RPC call.  In the future this is where features like HTTP Headers, websockets context, and other context objects would be passed in.
2. Change the implementation of the `http-api` and `ws-api` CLI and config options to be driven off of a map of namespaces instead of a Java Enum.  This will allow for downstream users to add custom namespaces.  
  
3. Update the `JsonRpcHttpService` and `WebSocketService` to respect the endpoints registered in point 1.

A prototype was implemented in Pantheon prior to the transition to Hyperledger Besu - [https://github.com/PegaSysEng/pantheon/pull/1909/files](https://github.com/PegaSysEng/pantheon/pull/1909/files)

# Alternatives Considered

- Not exposing a Plugin API  
Downstream consumers would need to patch Besu and ship a custom build of Besu to their customers.  This is considered less desirable because downstream users would have an increased maintenance burden to merge new versions of Besu into their custom versions.  This becomes very problematic when the changes include critical security vulnerability fixes.

# Testing

As with the other Plugin Services, a test plugin will be written and exercised as part of the acceptance tests.

  

# Backwards Compatibility

Introducing this API does not appear to introduce any backwards compatibility issues.  This represents new functionality that is not replacing existing functionality.  One observable change is that the `http-api` and `ws-api` options will be able to expose new values.