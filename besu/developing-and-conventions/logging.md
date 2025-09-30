# Logging

# Logging

This project employs the logging facade [SLF4J](https://www.slf4j.org/), using [Apache Log4j 2.x](https://logging.apache.org/log4j/2.x/) as its backend. Accordingly, levels of detail can be specified as follows:

OFF: The highest possible rank and is intended to turn off logging. ERROR: Designates error events that might still allow the application to continue running. WARN: Designates potentially harmful situations. INFO: Designates informational messages that highlight the progress of the application at coarse-grained level. DEBUG: Designates fine-grained informational events that are most useful to debug an application. TRACE: Designates finer-grained informational events than the DEBUG. ALL: All levels including custom levels.

For more guidance on which level to use, see [Coding Conventions#Logging](../developing-and-conventions/coding-conventions.md)

For modifying the log output of a running client, you may use a custom log4j config file by setting a system property at startup.  [Besu's logging doc](https://besu.hyperledger.org/public-networks/how-to/monitor/logging) provides good documentation on how to configure logging in Besu.