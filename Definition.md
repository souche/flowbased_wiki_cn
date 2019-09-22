> **Flow-based programming (FBP)** is a [Dataflow programming](http://en.wikipedia.org/wiki/Dataflow_programming) paradigm with a unique set of characteristics on one hand and a kind of [Component-based software engineering](http://en.wikipedia.org/wiki/Component-based_software_engineering) approach on the other hand. It was created by [J Paul Morrison](http://www.jpaulmorrison.com/) while working for IBM in 1970s.

**Flow-based programming (FBP)** 是一种 [Dataflow programming](http://en.wikipedia.org/wiki/Dataflow_programming) 范例，一方面具有独特的特征集，另一方面具有[Component-based software engineering](http://en.wikipedia.org/wiki/Component-based_software_engineering) 的特征。

> Flow-based programming considers an application as a set of processes ("black boxes") communicating via connections, which the processes access by means of "ports". A process is an instance of a component, running concurrently with other processes, including potentially other instances of the same component. The representation is a directed graph consisting of processes as nodes and connections as edges. For application developers, components will normally be treated as black boxes, but they can be whiteboxed if the developer needs to create a new component (usually done using a conventional, textual, programming language), or if the component is implemented as a subgraph.  In the latter case, the user can move between different levels of the graph. 

Flow-based programming 将应用程序视为通过连接（connections）进行通信的一组进程（“黑匣子”），这些进程通过“端口（ports）”进行访问。 进程是组件（component）的一个实例，与其他进程（包括同一组件的其他潜在实例）同时运行。 具体的表现就是由进程表示节点，由连接表示流动。 对于应用程序开发人员，组件通常将被视为黑盒，但是如果开发人员需要创建新组件（通常使用常规的文本编程语言来完成），或者如果组件被实现为子视图，则可以将其白盒化。 在后一种情况下，用户可以在图表的不同层级之间移动。

> The general approach in FBP is to conceptualize a program as a series of streams and substreams that flow through a series of connected processes. Parallelism and concurrency are enabled by restricting communication between processes to use streams of Information Packets ("passive" data) - shared memory problems are avoided by the rule that an Information Packet may only be "owned" (directly or indirectly) by a single process at a time.

FBP 中的一般方法是将程序概念化为流经一系列连接过程的一系列流和子流。 通过限制进程之间的通信以使用信息包流（“被动”数据）来启用并行性和并发性-通过规则，即信息包一次只能由单个进程“拥有”（直接或间接）来避免共享内存问题。

> Visual programming in this context is about connecting textual components and/or graphs in a bi-dimensional representation, which takes advantage of humans' pattern recognition abilities and visual styles of thinking. Textual programming is still available at the component level, and, for simple applications, at the network level.

在这种情况下，可视化编程是以一种二维的文本组件或者图形连接的表现形式，它利用了人类的模式识别能力和视觉思维方式。对于简单的网络级别的应用程序，或者组件级别，文本编程仍然可用。

> The main motivators are code reuse, testability, concurrency and maintainability.

它主要的意义是代码重用、可测试性、并发性和可维护性。

## Characteristics of Flow-based programming

FBP is often confused with Dataflow programming, but in fact it is a subset of Dataflow programming with the following unique properties:
 - Structural: graphs are structured; components have structure too (interface, state and behavior).
 - System design is split into 2 layers: graph layer (usually visual) and component layer (usually textual). From the software architecture point of view different roles are encouraged, the "graph designer" and the "component implementor".
 - Parallel: each FBP process runs in its own thread, coroutine or other concurrency facility.
 - Activation: From the graph designer point of view processes are running concurrently, and it is the function of the scheduling software to allocate CPU time and manage other services as required to maintain this illusion. 
 - Information packets have a life cycle and are owned explicitly by one process at a time.
 - Processes can be stateful.
 - Components can have multiple inputs or outputs.
 - Ports may be elementary ports or array ports, where the individual elements are treated as separate ports, but are addressed by port name plus an index.
 - The application is a graph rather than a tree. Cyclic connections (feedback loops) are allowed.
 - Connections can be merged in the graph, implying that packets from different arcs arrive at the input port in FIFO order. Connections should be split explicitly via a component because of the variety of splitting strategies and the explicit IP ownership rule.
 - Connections are implemented as bounded buffers with FIFO order and capacity from 0 to a number limited by implementation.
 - Data can own data. A packet can have sub packets and components do not need to be aware of the owned data. Tree structures and dictionaries can be created like this.
 - Parameters are provided to component instances in the network definition by associating a data value with a particular input port. This concept is called "Initial IP" and its implementation details vary between FBP versions.

See [Concepts](Concepts) for further details.

## Flow-based programming 的特征

FBP 通常与 Dataflow 编程相混淆，但实际上，它是 Dataflow 编程的一个子集，具有以下独特的属性：
- 结构：图是结构化的；组件也拥有结构（接口，状态，行为）。
- 系统设计分为两层：图形层（通常是可视的）和组件层（通常是文本的）。从软件体系结构的角度来看，鼓励不同的角色参与，“可视化设计者”和“组件实现者”
- 并行：每个FBP进程都在其自己的线程，协程或其他并发工具中运行。
- 激活：从图形设计者的角度来看，进程是同时运行的，并且调度软件的功能是分配 CPU 时间并根据需要管理其他服务以模拟这种效果。
- 信息包具有生命周期，并且一次由一个进程明确拥有。
- 流程可以是有状态的。
- 组件可以具有多个输入或输出。
- 端口可以​​是基本端口或阵列端口，其中各个元素被视为单独的端口，但是可以通过端口名称加索引来寻址。
- 该应用程序是图形而不是树状结构。环形连接（循环回路）是被允许的。
- 可以在图中合并连接，这意味着来自不同轨迹的数据包将以 FIFO 顺序到达输入端口。由于拆分策略和显式 IP 所有权规则的多样性，应通过组件显式拆分连接。
- 连接被实现为有限的缓冲区、FIFO 顺序的，容量从 0 到一个有限的数字。
- 数据可以持有数据。数据包可以具有子数据包，并且组件不需要知道所拥有的数据。可以创建树状结构的数据或者字典数据。
- 通过将数据值与特定的输入端口相关联，将参数提供给网络定义中的组件实例。此概念称为“初始IP”，其实现细节在FBP版本之间有所不同。
