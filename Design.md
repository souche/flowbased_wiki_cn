This section will cover topics related to designing software with FBP.

##Introduction
Designing systems with FBP opens different roads for software design and implementation, and this section will summarize them.

##Roles
Working with FBP in a team will lend itself to different roles, one will be graph design and system architecture, and the other will be component implementation and design. High level components like "Generate Report A" will be exploded into its sub components and so on. The roles are not fixed because from the perspective of a component implementer designing the inner workings of a component may require designing a graph, and so forth. The separation of concerns is very important because problems are easier to slice and less communication overhead will occur.

##Output Backwards
This is a term that describes a possible sequence for deciding which processes in your high-level design to flesh out first.  “Output-backwards” means that you start with the outputs intended for human consumption, and work backwards deciding how this data is going to be generated. Some data will come from outside sources, using Readers or similar processes, but most will be the result of performing transforms on these sources. The designer will typically be moving from right to left across the network.

##Centre Out
This is also a useful way of developing an application, and also allows the application to be delivered in stages.  “Centre-out” means that you start with the core processes, usually the ones which do business logic, together with any required Collators and Splitters, and get them working using the simplest possible Reader and Display components. Fancy output formatting, input editing, etc., can then be added incrementally working out from the centre. This approach is really a kind of prototyping, as you can develop the main logic and check it out first, before investing effort in making the output pretty, making the application more robust, etc. At selected points along the way, you can demonstrate the system to potential customers, prospective users, your manager, or whomever.