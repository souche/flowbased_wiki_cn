Common terms in the flow-based world and their explanation. Below each paragraph represents a term. First it is given in bold as proposed by Morrison's book (if available), other versions are given in braces. Terms may link to articles with detailed description of principles behind them.

* **Array Port** - a Port with indexed slots, reads and writes to Array Ports require an index.
* **Bracket Information Packet** - a special Information Packet that indicates the presence of a Sub Stream. It can contain information itself and there are two kinds: opening brackets (denoting the start of a Sub Stream) and closing brackets (denoting the end of a Sub Stream). They can be nested as needed.
* **Capacity** - max. number of information packets that can be buffered within a connection at a time.
* **Component** - a black box processing data, a most common building block in FBP. _Syn.: class (OOP), processor (DSP)._
* **Connection** - a connection between components through which data flows. _Syn.: pipe (POSIX), buffer (Protocol Buffers), message queue (AMQP), channel (CSP), line (DSP)._
* **Edge** - a static definition of a Connection within a Graph. _Syn.: arc._
* **Epoch** - elementary unit of system lifetime. _Syn.: tact, tick (DSP)._
* **Graph** - structural representation of an application as a network of components and connections between them.
* **Information packet** - a unit of data flow exchanged across components. _Syn.: message (OOP), record (RDMBS), tuple (Linda)._
* **Initial information packet** - a Packet utilized as process configuration that comes to existence when a read is issued, not triggering the configured process. _Syn.: parameter (IDEF0)._
* **Looper** - resident process.
* **Nest** - a part of the flow graph with intensive internal communication which is attached to the same physical or virtual machine or OS thread/process for high efficiency and may have its own scheduler. Remote nests are connected via network into a distributed application graph. _Syn.: island, section._
* **Net** - a running instance of **Graph**.
* **Node** - a generic term for a process or a subnet in a graph that is not running yet.
* **Non-looper** - a non-resident process which quits right after performing its task.
* **Port** - a connection point in a component through which it sends or receives data. Ports are one way, either OUT or IN.
* **Process** - an instance of a component being executed in runtime. Each component may spawn one or several processes. _Syn.: object (OOP), filter (DSP)._
* **Stream** - a sequence of information packets transmitted from one component to another. _Syn.: signal (DSP)._
* **Subnet** - a graph that exposes inports and outports and is reused as a component itself. _Syn.: subgraph, composite component._
* **Substream** - a stream nested within another (parent) stream and containing control (bracket) IPs.
* **Thread** - operating system parallel execution primitive with shared memory.