# DRAFT - Pico CLI Plugin Integration

> [!NOTE]
> This is a draft design document.

The current integration provided for plugin CLI integrations needs re-thinking. The main issue with the current implementation is around the ordering of when the CLI args get parsed by Pico and when the CLI command arguments are registered in a plugin.

As it stands, the earliest time you can `addPicoCLIOptions` is during plugin register. The problem here is that register is called fairly late in the bootstrap process of `BesuCommand`. There is also a conflation of responsibilities around CLI parameter validation.

## Example Plugin

Let's say we create a plugin that will be used to sign private transactions and we wish to enable it with a CLI argument `--plugin-signer-enabled`.

When Besu starts we want to validate that we've configured everything correctly. In this example, we want to validate that when privacy is enabled and we are using a network that has gas fees, we have a way of signing marker transactions. This means that you must either have a `--privacy-marker-transaction-signing-key-file` registered, or have registered a plugin to do the signing. The problem is that when the register method in the plugin is called, the CLI argument is not bound. But we must register the signer at this point because the validation happens before the start method is called.

## Proposals

Separate responsibility for registering and loading CLI options. Besu and all plugins should have all their CLI options loaded and available when the plugin methods are called. This will mean changing the way CLI plugin arguments are registered.

### Different registration process

A couple of options:

1. Mixin anything that implements `BesuPlugin`. This would mean that the plugin developer would only need to add the option into the class. It could lead to larger classes with mixed responsibility.
2. Add another method to the lifecycle. This would allow plugin developers to `addPicoCLIOptions` early in the lifecycle.

### Changing the bootstrap flow

One thing that would really help clarify responsibilities would be to clarify the bootstrap flow:

1. Parse, validate and load arguments.
   1. This will only check for validity of single arguments, e.g. type checking/enum checking.
   2. The end config result should be the same no matter what process you use, e.g. env variable vs toml etc.
2. Instantiate all exposed Plugin Services (e.g. `StorageService` etc).
   1. Currently, some services are not registered until after things have been created, e.g. `BesuEvents`. This should be our problem, not the plugin developer's problem.
3. Register all plugins.
4. Validate configuration combinations.
5. Instantiate Besu.
6. Run Besu.

## Code

Breaking changes POC for loading CLI options. This offers better integration and understanding of what's going on, but at the cost of being a breaking change. It also has less flexibility and means that CLI options are 'special'.

[besu-eth/besu#2768](https://github.com/besu-eth/besu/pull/2768)

Another option could be to introduce another method that would be called before `BesuPlugin::register` (and parse in besu) that would be specifically for registering CLI options.

[besu-eth/besu#2792](https://github.com/besu-eth/besu/pull/2792)
