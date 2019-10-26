# Introduction
> FBP is focused on the abstraction of asynchronous machines working together, and there are many ways to simulate that behavior. Green or Red threads, event loop or network of computers, and other choices can affect the implementation, but the graph and component design are going to be similar if FBP concepts are used.

fbp关注的是异步机协同工作的抽象，有很多方法可以模拟这种行为。绿色或红色线程、事件循环或计算机网络以及其他选择都可能影响实现，但是如果使用fbp概念，图形和组件设计将是相似的。

## Classical FBP
> This is the original approach, operative system or virtual machine threads are used, processes read and write concurrently, picking which ports are used to read, write and disconnect. Blocking reads and writes are present, and most of the advanced features are implemented.
Examples are : JavaFBP, THREADS, C#FBP.

这是最初的方法，使用操作系统或虚拟机线程，同时处理读和写，选择哪些端口用于读、写和断开连接。存在阻塞读写，并且实现了大多数高级功能.
例如：JavaFBP, THREADS, C#FBP.

## Reactive FBP
> This approach is "evented", where processes operate by waiting on events like connects, disconnects, sends, etc., and only control the sends and disconnects. They can also provide other mechanisms for doing manual receives/reads but the overall component design is built around event listeners.
Examples are NoFlo and microflo.

这种方法是“evented”，即进程通过等待连接、断开连接、发送等事件来操作，并且只控制发送和断开连接。它们还可以提供执行手动接收/读取的其他机制，但总体组件设计是围绕事件侦听器构建的。
比如NoFlo and microflo的例子

## "Litmus test"
> To differentiate the flavor of FBP you are dealing with, ask yourself if selective reads are present. Can you express your data requirements for an operation as a sequence of reads or do you have to encode a state machine that feeds on events?

> In this trivial example we create a component that reads two numbers from two ports and sends the greater of them through the GT port and the lesser through LT.

为了区分你正在处理的FBP的特色，问问自己是否存在选择性阅读。您是否可以将操作的数据需求表示为一个读取序列，或者您是否必须对以事件为源的状态机进行编码？

在这个简单的示例中，我们创建了一个组件，它从两个端口读取两个数字，并通过gt端口发送其中较大的数字，通过lt发送较小的数字。

Classical ( in pseudo java )  经典的
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
Reactive ( in javascript )  响应式的

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