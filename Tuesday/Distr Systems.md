# Design Decisions for Communication Systems
* Eric Anderson – Google; gRPC
GitHub/Gitter: @ejona86
Email: ejona@google.com (please CC mailing list)
Mailing List: grpc-io@googlegroups.com


See slides

# Shared Resources
* File
* File+file locks
* RDMA

# Common for desktop applications
* Common for intra-app communication
* High performance
* Brittle, but adding restrictions makes manageable
  * Poorly suited for crossing trust domains
  * Poorly suited to outgrow a single specific job
* Common patterns, but will be application-specific protocol
* Bit too complex and varied to get into
* When scaling over many machines, can still share resources via a network protocol
  * Many interaction patterns still hold

# Sockets
* Duplex stream of bytes or messages
* Point-to-point
* Client-server
  * The server binds to a port or name that the client knows toconnect to
* Connection-oriented
* Unix Domain Socket (bytes or messages)
* TCP (bytes)
  * Messages may have a maximum size
* UDP (messages)
  * Except it isn’t ordered
  * Except it doesn’t guarantee delivery
  * Except it doesn’t have flow control
  * Except it isn’t connection-oriented
  * Except it can multicast to multiple receivers
  * Yeah... let’s stop talking about UDP

