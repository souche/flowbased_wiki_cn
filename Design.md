
> This section will cover topics related to designing software with FBP.

这一部分，将涉及一些在使用 `FBP` 进行程序设计过程中的话题。

> ## Introduction
> Designing systems with FBP opens different roads for software design and implementation, and this section will summarize them.

## 简介
使用`FBP`设计系统，为软件设计和实现打开了不同的路，本文将总结这些不同。


> ## Roles
## 角色

> Working with FBP in a team will lend itself to different roles, one will be graph design and system architecture, and the other will be component implementation and design. 

工作在一个 `FBP` 团队里，会有不同的角色去承担。其中一个就是 可视化设计者与系统架构者，另一个则是 组件实现者。


> High level components like "Generate Report A" will be exploded into its sub components and so on.The roles are not fixed because from the perspective of a component implementer designing the inner workings of a component may require designing a graph, and so forth. 

在一些由分解成它的子组件组件的高级组件里，比如像 “生成报表A” 等组件。角色的划分就并不完全固定，因为，从一个组件实现者的角度来看，组件内部的运作，可能需要可视化设计等工作。

> The separation of concerns is very important because problems are easier to slice and less communication overhead will occur.

这种关注度的分离，是十分重要的。因为问题将会更容易被分解，需要的交流也更少。

> ## Output Backwards
## 输出逆推

> This is a term that describes a possible sequence for deciding which processes in your high-level design to flesh out first.  “Output-backwards” means that you start with the outputs intended for human consumption, and work backwards deciding how this data is going to be generated.

这是描述在你的高阶组件设计过程中，为了决定出哪一部分先实现出来的一个合理顺序的术语。
“Output-backwards” 意味着，你将需要先从人们所消费的输出（考虑），并反向去思考决定数据应该怎么被生产出来。

> Some data will come from outside sources, using Readers or similar processes, but most will be the result of performing transforms on these sources. The designer will typically be moving from right to left across the network.

有些数据从外部源获取，使用 `阅读器` 或者类似的程序，但大部分的数据都是对这些外部源上进行一些转换。可视化设计者通常从网络（图层）的右边到左边的方向进行思考与设计。

> ## Centre Out
## 挑出核心

> This is also a useful way of developing an application, and also allows the application to be delivered in stages.  “Centre-out” means that you start with the core processes, usually the ones which do business logic, together with any required Collators and Splitters, and get them working using the simplest possible Reader and Display components. 

这当然也是开发一个程序的好用的方法，同时它也允许程序分部发布。
“Centre-out” 意味着你将先从通常是商业逻辑的核心部分开始，让它与那些需要`收集器`与`分隔器`的程序，并使他们使用尽可能简单的`阅读器`与展示组件。

> This approach is really a kind of prototyping, as you can develop the main logic and check it out first, before investing effort in making the output pretty, making the application more robust, etc.

复杂的输出转换、输入编辑等，可以在这个核心组件逐渐增加并实现出来。这种方法，其实是原型开发的一种。你可以在投入更多精力让输出变得完美之前，先开发主要逻辑并验证它，这让程序更加具有鲁棒性。

> At selected points along the way, you can demonstrate the system to potential customers, prospective users, your manager, or whomever.

在开发的过程中，选择一些（阶段性的）点，可以让将你的系统展示给潜在的消费者、可能的用户以及你的老板或者其它任何一个人。
