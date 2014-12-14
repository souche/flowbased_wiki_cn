# Introduction
FBP is focused on the abstraction of asynchronous machines working together, and there are many ways to simulate that behavior. Green or Red threads, event loop or network of computers, and other choices can affect the implementation, but the graph and component design are going to be similar if FBP concepts are used.

## Classical FBP
This is the original approach, operative system or virtual machine threads are used, processes read and write concurrently, picking which ports are used to read, write and disconnect. Blocking reads and writes are present, and most of the advanced features are implemented.
Examples are : JavaFBP, THREADS, C#FBP.

## Reactive FBP
This approach is "evented", where processes operate by waiting on events like connects, disconnects, sends, etc., and only control the sends and disconnects. They can also provide other mechanisms for doing manual receives/reads but the overall component design is built around event listeners.
Examples are NoFlo and microflo.

## "Litmus test"
To differentiate the flavor of FBP you are dealing with, ask yourself if selective reads are present. Can you express your data requirements for an operation as a sequence of reads or do you have to encode a state machine that feeds on events?

In this trivial example we create a component that reads two numbers from two ports and sends the greater of them through the GT port and the lesser through LT.

Classical ( in pseudo java )
 ```java
    ... component code and setup
    Packet a = read("A");
    Packeg b = read("B");
    if( a.data() > b.data() ){
    send("GT", a);
    send("LT", b);
    } else {
    send("GT", b);
    send("LT", a);
    }
    ... etc
```
Reactive ( in javascript )

```javascript
    ... component code and setup
    inPorts.a.on('data', function(data, index){
      this.a = data;
      compare();
    }
    inPorts.b.on('data', function(data, index){
      this.b = data;
      compare();
    }
    function compare(){
     if( this.a !== null && this.b !== null ){
      if( this.a > this.b){
        outPorts.gt.send(a);
        outPorts.lt.send(b);
      }else{
        outPorts.gt.send(b);
        outPorts.lt.send(a);
      }
      this.a = null;
      this.b = null;
    }
    ... etc
```