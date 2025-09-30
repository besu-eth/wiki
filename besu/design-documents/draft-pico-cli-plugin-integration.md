# DRAFT - Pico CLI Plugin Integration

The current integration provided for plugin CLI integrations needs re-thining. The main issue with the current implementation is around the ordering of when the cli args get parsed by Pico and when the cli command arguments are registered in a plugin.

As it stands the earliest time you can addPicoCLIOptions is during plugin register. The problem here is that register is called fairly late in the bootstrap process of BesuCommand. There is also a conflation of responsibilities around cli parameter validation.

  

### Example Plugin

Let's say we create a plugin that will be used to sign private transactions and we wish to enable it with a cli argument --plugin-signer-enabled

When Besu starts we want to validate that we've configured everything correctly. In this example, we want to validate that when privacy is enabled and we are using a network that has gas fees we have a way of signing marker transactions. This means that you must either have a --privacy-marker-transaction-signing-key-file or registered or have registered a plugin to do the signing. The problem is that when the register method in the plugin is called the cli argument is not bound. But we must register the signer at this point because the validation happens before the start method is called.

  

### Proposals

Separate responsibility for registering and loading cli options. Besu and all Plugins should have all their cli options loaded and available when the plugin methods are called. This will mean changing the way cli plugin arguments are registered.

##### Different registration process

A couple of options:

1. Mixin anything that implements BesuPlugin - this would mean that the plugin developer would only need to add the option into the class. It could lead to larger classes with mixed responsibility.
2. Add another method to the lifecycle - this would allow plugin developers to addPicoCLIOptions early in the lifecycle.

##### Changing the bootstrap flow

I also think one thing that would really help clarify responsibilities would be to clarify the bootstrap flow.

1. Parse, validate and load arguments
  1. this will only check for validity of single arguments e.g type checking/enum checking
  2. the end config result should be the same no matter what process you use e.g env variable vs toml etc.
2. Instantiate all exposed Plugin Services (e.g StorageService etc)
  1. currently, some services are not registered until after things have been created e.g BesuEvents this should be our problem not the plugin developers problem.
3. Register all Plugins
4. Validate Configuration combinations
5. Instantiate Besu
6. Run Besu

### Code

Breaking changes POC for loading cli options - I think this offers better integration and understanding of what's going on but at the cost of being a breaking change. It also has less flexibility and is means that cli options are 'special'.

[https://github.com/hyperledger/besu/pull/2768](https://github.com/hyperledger/besu/pull/2768)

  

Another option could be to introduce another method that would be called before BesuPlugin::register (and parse in besu) that would be specifically for registering cli options.

[https://github.com/hyperledger/besu/pull/2792](https://github.com/hyperledger/besu/pull/2792)