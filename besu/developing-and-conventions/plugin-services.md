# Plugin Services

Since the deprecation of bintray and jcenter javadocs are no longer being consumed by [https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/index.html](https://javadoc.io/doc/org.hyperledger.besu/plugin-api/latest/index.html)

This is a temporary measure until we start hosting our own javadocs

A manual snapshot was taken on 11 Oct 2021

  

  

# Package org.hyperledger.besu.plugin.services

Interface Summary

| Interface | Description |
| --- | --- |
| BesuConfiguration | Generally useful configuration provided by Besu. |
| BesuEvents | This service allows plugins to attach to various events during the normal operation of Besu. |
| BesuEvents.BlockAddedListener | The listener interface for receiving new block added events. |
| BesuEvents.BlockPropagatedListener | The listener interface for receiving new block propagated events. |
| BesuEvents.BlockReorgListener | The listener interface for receiving new block reorg events. |
| BesuEvents.LogListener | The listener interface for receiving log events. |
| BesuEvents.SyncStatusListener | The listener interface for receiving sync status events. |
| BesuEvents.TransactionAddedListener | The listener interface for receiving new transaction added events. |
| BesuEvents.TransactionDroppedListener | The listener interface for receiving transaction dropped events. |
| BesuService | All services that can be resolved via [`BesuContext.getService(Class)`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/BesuContext.html#getService(java.lang.Class)) must implement [`BesuService`](http://localhost:63342/besu/besu.plugin-api/build/docs/javadoc/org/hyperledger/besu/plugin/services/BesuService.html) |
| MetricsSystem | An interface for creating various Metrics components. |
| [PermissioningService](./plugin-services/permissioningservice.md) | This service allows plugins to decide who you should connect to and what you should send them. |
| PicoCLIOptions | A service that plugins can use to add CLI options and commands to the BesuCommand. |
| PluginVersionsProvider |     |
| [PrivacyPluginService](./plugin-services/privacypluginservice.md) | A service that plugins can use to define how private transactions should be handled. |
| [RpcEndpointService](./plugin-services/rpcendpointservice.md) | This service allows you to add functions exposed via RPC endpoints. |
| SecurityModuleService | This service allows plugins to register a Security Module, which is abstraction of cryptographic operations that defer to specific provider (e.g. |
| StorageService | This service allows plugins to register as an available storage engine. |