# Terminology

Common terms in the flow-based world and their explanation. Below each paragraph represents a term. First it is given in bold as proposed by Morrison's book (if available), other versions are given in braces. Terms may link to articles with detailed description of principles behind them.

* **Capacity** - max. number of information packets that can be buffered within a connection at a time.
* **Component** (same in Component-based systems; auton - Aristophanes, class - OOP, processor - DSP) - a black box processing data, a most common building block in FBP.
* **Connection** (pipe - POSIX pipes, Hartmann pipeline, buffer - Protocol Buffers; channel - CSP, Go; line - DSP) - connection between components through which data flows.
* **Epoch** (tact, tick - DSP) - elementary unit of system lifetime.
* **Graph** - structural representation of an application as a network of components and connections between them.
* **Information packet** (same in OSI/ISO; message - OOP, Protocol Buffers; record - RDMBS; tuple - Linda) - unit of data flow exchanged across components.
* **Initial information packet** (also parameter; control input - IDEF0) - special type of data which modifies external parameters of the process functioning.
* **Looper** - resident process.
* **Nest** (term by Aristophanes; island, section - Ohua) - a part of the flow graph with intensive internal communication which is attached to the same OS thread/process for high efficiency and may have its own scheduler.
* **Net** - same as **Graph** or a a running **Graph**.
* **Non-looper** - a non-resident process which quits right after performing its task.
* **Port** (same in Component-based systems, DSP, Berkley sockets; channel - CSP, Go) - a connection point in a component through which it sends or receives data.
* **Process** (object - OOP; coroutine - CSP) - an instance of a component being executed in runtime. Each component may spawn one or several processes.
* **Stream** (signal - DSP) - a sequence of information packets transmitted from one component to another.
* **Subnet** - a part of a net being a net itself.
* **Substream** - a stream nested within another (parent) stream.
* **Thread** - operating system parallel execution primitive with shared memory.