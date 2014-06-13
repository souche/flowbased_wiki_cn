**Flow-based programming (FBP)** is a [Dataflow programming](http://en.wikipedia.org/wiki/Dataflow_programming) paradigm with a unique set of characteristics on one hand and a kind of [Component-based software engineering](http://en.wikipedia.org/wiki/Component-based_software_engineering) approach on the other hand. It was created by [J Paul Morrison](http://www.jpaulmorrison.com/) while working for IBM in 1970s.

Flow-based programming considers an application as a set of components ("black boxes") connected through ports. The representation is a directed graph consisting of components as nodes and connections as edges. Each component in the graph can also be seen as a "white box", which is either a nested graph (subgraph) or a subprogram in a conventional programming language (usually textual). The approach is to conceptualize a program as a series of streams and substreams that flow through a series of connected components. Parallelism and concurrency are enabled by communicating with Information Packets ( dumb data ) and avoiding shared memory problems. Visual programming in this context is about connecting textual components and/or graphs in a bi dimensional representation and not a way of replacing textual programming.
The main motivators are code reuse, testability, concurrency and maintainability.

## Characteristics of Flow-based programming

FBP is often confused with Dataflow programming, but in fact it is a subset of Dataflow programming with the following unique properties:
 - Structural: graphs are structured, components have structure too (interface, state and behavior).
 - System design is split into 2 layers: graph layer (usually visual) and component layer (usually textual). From the software architecture point of view different roles are encouraged, the "graph designer" and the "component implementor".
 - Parallel: each component runs in its own process, thread, coroutine or other concurrency facility.
 - Activation: From the graph designer point of view all processes are running all the time, and the library should handle activations accordingly to maintain this illusion.
 - Information packets have a life cycle and are owned explicitly by one process at a time.
 - Components can be stateful.
 - Components can have multiple inputs or outputs.
 - The application is a graph rather than a tree. Cyclic connections (feedback loops) are allowed.
 - Connections can be merged in the graph, implicating that packets from different arcs arrive at the input port in FIFO order. Connections should be split explicitly via a component because of the variety of splitting strategies and the explicit IP ownership rule.
 - Connections are implemented as bounded buffers with FIFO order and capacity from 0 to a number limited by implementation.
 - Data can own data. A packet can have sub packets and components do not need to be aware of the owned data. Tree structures and dictionaries can be created like this.

See [Concepts](Concepts) for further details.