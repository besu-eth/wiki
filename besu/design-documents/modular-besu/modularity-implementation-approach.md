# Modularity Implementation Approach

# Context

Making Besu more modular requires thinking about the dimensions along which those modules are divided up and separated from each other. Those separations can be categorized into two types: areas of related business logic, and areas of related software function. The former is the domain of "stuff Ethereum needs" and the later is the domain of "stuff good Java software needs". When we modularize Besu, we are looking to produce reusable, composable software components within the business logic domain.  

Bounded Contexts / Business Logic / Blockchain Domain are all synonyms for the type of modules we want to create to serve the pillars of our 2022 Vision. We will know we are doing this right when users can easily create a Besu that combines different modules into the client they need.

Cross Cutting Concerns are a little bit different. These should be invisible to the users, but very helpful to the developers. Any Bounded Context may depend on any mix of Cross Cutting Concerns. This part is ok to be a web of dependencies, they are often external projects/libraries we have selected for use all throughout Besu.

  

| Business Logic | Cross Cutting Concerns |
| --- | --- |
| 1. Consensus<br>  1. Proof of Work<br>  2. External (or none?): Proof of Stake<br>    1. driven by Engine API<br>  3. Clique<br>  4. IBFT<br>  5. QBFT<br>2. P2P<br>  1. ETH/66 and prior<br>  2. DevP2P<br>3. Execution<br>  1. EVM<br>  2. Tracing<br>4. Transaction Management<br>  1. Tessera integration<br>  2. MEV<br>  3. public and private transaction support<br>  4. Proof of work tx validation<br>5. Synchronizing<br>  1. Full sync<br>  2. Fast sync<br>  3. Snap sync<br>  4. Checkpoint sync<br>  5. Backwards sync<br>6. Storage<br>  1. World State<br>    1. Forest<br>    2. Bonsai<br>    3. Snapshot (RocksDB specific)<br>    4. Verkle<br>  2. Blockchain <br>  3. Key-Value specific implementations under each. | 1. Cryptography<br>  1. Elliptic Curves<br>  2. Signatures<br>  3. Hashing<br>  4. native implementations<br>2. Serialization<br>  1. RLP<br>  2. JSON<br>  3. GraphQL(ish. it's a lot broader than just serialization)<br>3. APIs<br>  1. RPC<br>    1. HTTP<br>    2. Websockets<br>  2. GraphQL<br>  3. IPC<br>4. Inversion of Control<br>  1. Dagger<br>  2. Spring<br>5. Observability<br>  1. Logging<br>  2. Metrics<br>  3. Debugging extras<br>6. Configuration<br>  1. PicoCLI<br>  2. Genesis state vs. named networks<br>7. Builds<br>  1. Static code analysis <br>  2. Use-case specific distributions<br>  3. test automation<br>    1. Unit<br>    2. Integration<br>    3. System<br>    4. Fuzz |

  

# Goals

1. Pick relevant modules for abstraction against the goals outlined in our [Modularity Design](../modular-besu.md). A good consideration is the rule of threes: we should only abstract a module when we have a need for it in three contexts.
2. Begin work on one abstraction 
  1. Document approach 
  2. Design implementation of interface or inversion of control
  3. Review software engineering practices with the working group
  4. Review code changes and implementation details with working group
3. Define success criteria for remaining modules
4. Template design work from one slice and share learnings
5. Determine remaining modules (what needs new abstraction, against our goals) 
6. Create working group plan and discuss division of work

# Proof of Concept:

Introduce Inversion of Control to implement a vertical slice of functionality. We need to find a feature that touches on a few cross-cutting concerns, but just one Bounded Context.

Nominees:

1. Transaction validation stack - touches each consensus mechanism, any L2 network, MEV, block building, and more. Good candidate. 
2. MetricsSystem - Each time we need to expose a metric, we need to get this MetricsSystem from upper Layers and transfer it from constructor to constructor. 
3. Configuration management - 
4. Jumpdest caching. Only relevant to the EVM, but requires caching, configuration, Observability, and hashing. Plan would be to provide each of these as a dependency.
5. PoA consensus mechanisms. Impact TBD.
6. Transaction pool. Impact TBD.
7. Merge Context. What if the Merge Coordinator and related classes could be a dagger module?
8. Protocol Schedule. Impact TBD.

Once the question of "will dependency injection make for cleaner composition of modules into an application" is answered, we can then start to incrementally adopt it within each bounded context, and across the cross-cutting concerns.