**Flow-based programming (FBP)** is a [Dataflow programming](http://en.wikipedia.org/wiki/Dataflow_programming) paradigm with a unique set of characteristics on one hand and a kind of [Component-based software engineering](http://en.wikipedia.org/wiki/Component-based_software_engineering) approach on the other hand. It was created by [J Paul Morrison](http://www.jpaulmorrison.com/) while working for IBM in 1970s.

Flow-based programming considers an application as a set of processes ("black boxes") connected through ports. A process is an instance of a component, running concurrently with other processes, including potentially other instances of the same component. The representation is a directed graph consisting of processes as nodes and connections as edges. For application developers, components will normally be treated as black boxes, but they can be whiteboxed if the developer needs to create a new component (usually done using a conventional, textual, programming language), or if the component is implemented as a subgraph.  In the latter case, the user can move between different levels of the graph. 

The general approach in FBP is to conceptualize a program as a series of streams and substreams that flow through a series of connected processes. Parallelism and concurrency are enabled by restricting communication between processes to use streams of Information Packets ("passive" data) - shared memory problems are avoided by the rule that an Information Packet may only be "owned" (directly or indirectly) by a single process at a time.

Visual programming in this context is about connecting textual components and/or graphs in a bi-dimensional representation, which takes advantage of humans' pattern recognition abilities and visual styles of thinking. Textual programming is still available at the component level, and, for simple applications, at the network level.

The main motivators are code reuse, testability, concurrency and maintainability.

## Characteristics of Flow-based programming

FBP is often confused with Dataflow programming, but in fact it is a subset of Dataflow programming with the following unique properties:
 - Structural: graphs are structured; components have structure too (interface, state and behavior).
 - System design is split into 2 layers: graph layer (usually visual) and component layer (usually textual). From the software architecture point of view different roles are encouraged, the "graph designer" and the "component implementor".
 - Parallel: each FBP process runs in its own thread, coroutine or other concurrency facility.
 - Activation: From the graph designer point of view processes are running concurrently, and it is the function of the scheduling software to allocate CPU time and manage other services as required to maintain this illusion. 
 - Information packets have a life cycle and are owned explicitly by one process at a time.
 - Processes can be stateful.
 - Components can have multiple inputs or outputs.
 - Ports maybe elementary ports or array ports, where the individual elements are treated as separate ports, but are addressed by port name plus and index.
 - The application is a graph rather than a tree. Cyclic connections (feedback loops) are allowed.
 - Connections can be merged in the graph, implicating that packets from different arcs arrive at the input port in FIFO order. Connections should be split explicitly via a component because of the variety of splitting strategies and the explicit IP ownership rule.
 - Connections are implemented as bounded buffers with FIFO order and capacity from 0 to a number limited by implementation.
 - Data can own data. A packet can have sub packets and components do not need to be aware of the owned data. Tree structures and dictionaries can be created like this.
 - Given that FBP is component-oriented, there has to be a way in the network definition to provide parameters to component instances.  In current FBP implementations, this is usually done by associating a data value with a particular input port.  Actual implementation details vary between FBP versions.

See [Concepts](Concepts) for further details.