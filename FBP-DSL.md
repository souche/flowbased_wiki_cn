# FBP Domain Specific Language

The current language used to describe graphs textually is an implementation of Stevenson's DSL, and it looks like this:

Declaring a process:

    ProcessName(packageName/ComponentName)

Example:

    ReadLog(filesystem/ReadText)

Connecting an output to an input:

    ReadLog(filesystem/ReadText) OUT -> IN WriteLog(filesystem/WriteText)

This means that the port 'OUT' of ReadLog is going to be connected to the port 'IN' of WriteLog.
Connections can be chained together too.
Subsequent uses of a process do not require specifying the package and component name again.
Comments are marked with a #.
