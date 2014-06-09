**Flow-based programming (FBP)** is a [Dataflow programming](http://en.wikipedia.org/wiki/Dataflow_programming) paradigm with a unique set of characteristics on one hand and a kind of [Component-based software engineering](http://en.wikipedia.org/wiki/Component-based_software_engineering) approach on the other hand.

Flow-based programming considers an application as a set of components ("black boxes") and connections between them. In other words, application is a graph consisting of components linked by connections. Each component in the graph can also be seen as a "white box", which is either a nested graph (subgraph) or a subprogram in a conventional programming language (usually textual). The approach is mostly focused on on data flowing in form of Information Packets (IPs) between the nodes, rather than control flow in particular subprograms.

## Characteristics of Flow-based programming

FBP is often confused with Dataflow programming, but in fact it is a subset of Dataflow programming with the following unique properties:
 - Structural: graphs are structured, components have structure too (interface, state and behavior).
 - System design is split into 2 layers: graph layer (usually visual) and component layer (usually textual).
 - Parallel: each component runs in its own process, thread, coroutine or other concurrency facility.
 - Asynchronous activation: 
 - Data is encouraged to be immutable, but it is not a must. Information packets can be mutable, each IP has its lifecycle and is owned explicitly by one process at a time.
 - Components can be stateful.
 - Components can have multiple inputs or outputs.
 - Application is a graph rather than a tree. Cyclic connections (feedback loops) are allowed.
 - Connections are implemented as bounded buffers with FIFO order and capacity from 0 to a number limited by implementation.

See [Concepts](Concepts) for further details.