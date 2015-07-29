# FBP Domain Specific Language

The current language used to describe graphs textually is an implementation of Stevenson's DSL, and it looks like this:

Declaring a process:
    ProcessName(packageName/ComponentName)

Comments are marked with a #.

Example:

    # This is a comment
    ReadLog(filesystem/ReadText)

Connecting an output to an input:

    ReadLog(filesystem/ReadText) OUT -> IN WriteLog(filesystem/WriteText)

This means that the port 'OUT' of ReadLog is going to be connected to the port 'IN' of WriteLog.
Connections can be chained together too.
Subsequent uses of a process do not require specifying the package and component name again.

Initial Information Packets:

    'Hello World' -> IN Log(core/Output)

Data to be used as IIPs is enclosed in single quotes, the FBP engine loading the graph is responsible for the interpretation of this string.

Array ports:

    Splitter(core/Split) OUT[1] -> IN[0] WriteLog(filesystem/WriteText)

Brackets with an integer next to a port name denote its index for the connection.
The javascript implementation of the parser assumes order of declaration as the index automatically, but this is not a characteristic of the DSL.

Connections can be chained like this :

    'rawdata.txt' -> IN Read() OUT -> IN Compute() OUT -> IN Alter() OUT -> RESULTS Report()

Repeating connections do not affect the graph and can serve as additional detail when documenting functionality.
