Advanced features help simplifying common tasks or solving very specific problems. They are not required from every FBP implementation because they are only necessary in a limited subset of application domains, or because they can be emulated with other basic features.

## Data features

### Substreams

TODO: add description here

### Tree-like IPs

TODO: add description here

## Port features

### Array ports

Ports that have indexes , and each index can be connected to a port. The user can read and write to independent indexes as will. Same rules apply as if it was a normal port for blocking.
In pseudo-code, reading to the index 4 of port "IN" would be:

`Packet p = read("IN", 4);`

or

`Packet p = inports["IN"].read(4)`

etc.

And a send would be:

`send(p, "OUT",4);`

The important idea is that the index of incoming and outgoing packets is known.

### Automatic ports

TODO: add description here

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

### Pull-type processes

TODO: add description here

### Deadlock detection

Some applications have built-in facilities to detect or prevent deadlocks between processes.

### Recursive graphs

Recursive graphs can refer to and embed themselves, making recursive data processing possible the visual way.

## Dynamic structure

Initially FBP applications are static: once an application graph is started, it cannot add or remove nodes. Some implementations allow changing application structure at run-time, making it more flexible on one hand and less reliable on the other.

Allowing modifications to the running graph can be useful when developing iteratively.