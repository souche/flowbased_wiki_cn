This section explains common patterns for flow control.

## Concatenate:
### Description:
This component exposes an array IN port, and waits for all connections to close before forwarding their contents in order through OUT.
### Example usage:
Waiting for parameters coming from different flows to make a request.