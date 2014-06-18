This article introduces the basic concepts that any FBP implementation provides. It can be used as a brief description of how FBP works in general.

## Components

Components are the building blocks in Flow-based programming. This section covers elementary components which are usually written as classes, functions or small programs in conventional programming languages. For composite components see [Graphs section](Concepts#Graphs) below.

### Processes

A Process is an instance of a Component living in a Graph. The system should handle processes in the form of coroutines, threads or a similar form of concurrency, or at least provide the illusion of it to the graph designer. They should only be able to access their own internal state and ports but not much else about the graph itself and other processes.

### Connections

Processes communicate via connections, which the processes access by means of "ports". In "classical" FBP, connections are implemented via bounded buffers. 

### Ports

Ports are the points of contact between processes and connections. They are named, and may also be indexed if the port is an Array Port. The port name may be viewed as a contract between the component code and the network specification.  A Process can send and receive from any of the ports but should restrict itself to only a read or write operation at the same time.

#### Input ports

They provide a READ or RECEIVE functionality to dequeue messages from the buffer, and require an index in the case of Array Ports. Other features like obtaining the buffer load or which indexes have incoming packets in the case of array ports are desirable for simplifying the design and implementation of some components. An example of this would be an event handler.

In "classical" FBP, connections correspond 1:1 to (non-IIP) input ports or input array port elements.  If a connection becomes empty, the process being fed by that connection is suspended until more data IPs arrive (in "classical" FBP, this can only be one process).

#### Output ports

They provide a SEND functionality to queue the packet into the port of the connected process. Usually sends require a packet and the name of the port, or the send is a method and the output port is a known object.
If the connection fills up with packets, the process is suspended until the buffer is not full.

### Internal state

A Process, being an instance of a Component, can hold its internal state as long as it's active. An important part of FBP is keeping the state private and only interacting via port actions with other processes.

### Data processing

In FBP data processing is focused on handling streams of packets and embedded sub streams. The common analogy is to think about a series of machines that communicate with conveyor belts, each with its own inputs and ouput ports. Designs should be oriented to data transformations and filtering. Since data between each process is buffered, asynchronous operation is achieved, freeing the developer from additional logic to handle it.
Another interesting idea is that bypassing a process is trivial, and so is storing intermediate steps.

## Information packets

Information packets are in constant debate, but at the end of the day it depends on the application domain. The general consensus is that the packet should carry data that is serializable and passive in its nature. Sending an instantiated Video Player in a packet is an example of what should not be done, and instead sending the individual frames would be the correct approach.
The packet should contain a reusable data type, and depending on the implementation, allow for features like adding dictionary entries with other packets as values, attaching packets as siblings forming tree structures, ownership to stop other processes from altering a packet, schemas for validating dictionary entries, etc. 

### Initial information packets
In a Graph , each Process can have several Initial Information Packets that serve as configuration. They do not get pushed into a port until the process issues a RECEIVE or READ on that port. Think of them as passive packets.

### Activation

A Process is activated when it has incoming packets on its input ports, an exception of this would be a Start component in some implementations that is designed to be started on Graph activation and it forwards the IIPs attached to it.
IIPs should not activate a process, although some implementations do.


## Connections

TODO: add description here

### Capacity

### Merging

TODO: add description here

## Graphs

TODO: add description here

### External ports

TODO: add description here

### Feedback loops

TODO: add description here

## Flow features

This section covers aspects of how applications work in general.

### Resident and non-resident processes

TODO: add description here (in the FBP book it is called "Loopers" and "Non-loopers")