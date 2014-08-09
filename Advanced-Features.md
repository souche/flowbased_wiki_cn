Advanced features help simplifying common tasks or solving very specific problems. They are not a requirement in every FBP implementation because they are only necessary in a limited subset of application domains, or because they can be emulated with other basic features.

## Data features

### Sub Streams

The basic control flow mechanism is through connects and disconnects, but packets can be grouped inside a stream for different purposes. For example grouping request responses by the packet used for the request, passing lists of packets, building tree structures in a stream , etc.
A group is denoted by **open** and **close** bracket information packets. They are the same as an information packet but they are tagged as brackets. For example if we have a component that makes requests to URLs sent to it, and then sends the responses, we can put responses inside a group with an open bracket whose data is the URL, the contents of the response, and then a close bracket whose data is the URL again.
To symbolize it we use the '<' and '>' symbols.
    
    < http://somewhere.com
    packet1
    packet2
    ...
    packetN
    > http://somewhere.com
    < http://awebpage.com
    packet1
    packet2
    ...
    packetN
    > http://awebpage.com

Groups can be nested as needed.

### Tree-like IPs

TODO: add description here

## Port features

### Array ports

Ports that have indexes, and each index can be connected to a port. The user can read and write to independent indices at will. Same rules apply as if it was a normal port for blocking.
In pseudo-code, reading to the index 4 of port "IN" would be:

`Packet p = read("IN", 4);`

or

`Packet p = inports["IN"].read(4);`

etc.

And a send would be:

`send(p, "OUT",4);`

The important idea is that the index of incoming and outgoing packets is known.

### Automatic ports

Not all ports need to be known to the components they are attached to: sometimes it is desirable to be able to specify connections in the network which the processes themselves don’t know about. These are especially useful for introducing timing constraints into an application without having to add logic to the components involved, and handling various kinds of error condition. One such type of port is what we call "automatic ports", to reflect the idea that their functioning is not under the component’s control.

There are two types of automatic ports: automatic input ports and automatic output ports.  The former acts as a delay: if an automatic input port is connected, process activation is delayed until an IP is received on that port, or until the port is closed. This assumes that no data has arrived at another input port.

The latter sends a signal when a process closes down, which can be used to trigger (or delay) actions downstream.  In both the JavaFBP and C#FBP implementations, the signal is actually a `close`, so there is no IP to be disposed of.

## Graph features

### Named connections

TODO: add description here

### Multiplexing factor

TODO: add description here

## Flow features

These are the features which affect application data and control flow in general.

### Blocking sends and back pressure

When a connection is at full capacity, successive sends are blocked until the connection has room for more packets, effectively pausing the execution of the sending process. This stops a process from bringing the system down by exhausting the resources, and the upstream process will control indirectly how much data will be produced by the downstream process.


### Non-blocking sends

Non blocking sends can be useful for operations that require a continuous stream of "newest" data, like sensor readings, dropping the oldest packets and avoiding downstream process blocking.

In JavaFBP and C#FBP, this is implemented by setting the attribute `dropOldest` to `true` in a particular connection in the network definition.

### Pull-type processes

TODO: add description here

### Deadlock detection

Some applications have built-in facilities to detect or prevent deadlocks between processes.

### Recursive graphs

Recursive graphs can refer to and embed themselves, making recursive data processing possible the visual way.

## Dynamic structure

Initially FBP applications are static: once an application graph is started, it cannot add or remove nodes. Some implementations allow changing application structure at run-time, making it more flexible on one hand and less reliable on the other.

Allowing modifications to the running graph can be useful when developing iteratively.