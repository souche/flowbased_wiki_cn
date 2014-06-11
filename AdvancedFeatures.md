Advanced features help simplifying common tasks or solving very specific problems. They are not required from every FBP implementation because they are only necessary in a limited subset of application domains, or because they can be emulated with other basic features.

## Data features

### Substreams

TODO: add description here

### Tree-like IPs

TODO: add description here

## Port features

### Array ports

TODO: add description here

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

TODO: add description here

### Non-blocking sends

TODO: add description here

### Pull-type processes

TODO: add description here

### Output backwards

TODO: add description here

### Deadlock detection

Some applications have built-in facilities to detect or prevent deadlocks.

### Recursive graphs

Recursive graphs can refer to and embed themselves, making recursive data processing possible the visual way.

## Dynamic structure

Initially FBP applications are static: once an application graph is started, it cannot add or remove nodes. Some implementations allow changing application structure at run-time, making it more flexible on one hand and less reliable on the other.