# Introduction
FBP is focused on the abstraction of asynchronous machines working together, and there are many ways to simulate that behavior. Green or Red threads, event loop or network of computers, and other choices can affect the implementation, but the graph and component design are going to be similar if FBP concepts are used.

## Classical FBP
This is the original approach, operative system or virtual machine threads are used, processes read and write concurrently, picking which ports are used to read, write and disconnect. Blocking reads and writes are present, and most of the advanced features are implemented.
Examples are : JavaFBP, THREADS, C#FBP.

## Reactive FBP
This approach is "evented", where processes operate by waiting on events like connects, disconnects, sends, etc., and only control the sends and disconnects. They can also provide other mechanisms for doing manual receives/reads but the overall component design is built around event listeners.
Examples are NoFlo and microflo.