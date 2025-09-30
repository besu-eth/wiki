# Debugging Besu in IntelliJ

Running Besu in debug mode within your IDE can be very useful as this allows you to set breakpoints on certain lines. You can also debug your forked version of the Besu repo in your current branch to confirm the behaviour of any intended changes. To do this in IntelliJ:

- Search for the Besu class (*shortcut: command + O* and enter ‘Besu’).
- Click on the green triangle to the left of the main method within the Besu class and select Modify Run Configuration to add CLI arguments as you would when running Besu on the terminal. Press apply and OK once done.
- Click on the green triangle again and select Debug ‘Besu.main()’.

Advanced: if you want to debug acceptance tests (that run multiple besu nodes in a cluster), you need to be using `ThreadBesuNodeRunner` as opposed to `ProcessBesuNodeRunner` which is the default.

- Otherwise your IDE will not stop at any breakpoints - which is kinda what you want when debugging
- You can set this property `acctests.runBesuAsProcess`
- or change the code here [https://github.com/hyperledger/besu/blob/bdb00b299e2ad8498f9ec70e961774ee0ec9ba9f/acceptance-tests/dsl/src/main/java/org/hyperledger/besu/tests/acceptance/dsl/node/BesuNodeRunner.java#L29](https://github.com/hyperledger/besu/blob/bdb00b299e2ad8498f9ec70e961774ee0ec9ba9f/acceptance-tests/dsl/src/main/java/org/hyperledger/besu/tests/acceptance/dsl/node/BesuNodeRunner.java#L29)