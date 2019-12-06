### Debugging live apps the k8s way: from a sidecar
Joe Elliott

Backend engineer at grafanalabs
Building a toolset container "a sidecar" to pack full of debug tools

Second part of talk is a demo

Technologies used for debugging
- perf - cpu profiling
- LTTng
- BCC (BPF) - dynamic tracing, uprobes

Why do debugging from a sidecar?
"SSH into a node. Learn more about process on my linux container"
Had a mess when installing binaries to linux. Don't like world where all nodes were consistent to each node that had debugging run had different sets of tooling. When sidecar goes away, the "mess" goes away.

Supports development diversity. Each team can build their own debugging container.

Why is it "easy" not easy?
Tooling might be kernel specific, which may be incompatible with the other kernel version. Minimized if there is only one kernel in cluster.

Sidecar image may be very large. Not a big deal, just for specialized moments. Pull time goes up.
Sidecars can't be loaded in dynamically (yet, at least until ephemeral containers are a thing).

"What elements of the pod spec are we going to be using?"
- `shareProcessNamespace` normally, each process is separated by namespace. This key allows one to allow the pod and sidecar to have their processes started in the same namespace.
- Sharing mounted volumes
- mounting host paths
- `securityContext.privileged`

The DEMO!
CPU Profiling.
Great for seeing which functions you app is lingering on. Samples the stack many times a second to determine which methods of our application spends the most time on.

Load up sidecar. Exec into sidecar. Generate "flame graph"
`ps x`

Static Tracepoint
Why do these exists? Designed for high volume. For protocol path. Record but with low impact on app (vs. logging, which is I/O)

Dynamic tracing
"New" have the kernel call back when a function is called.

You need to figure out where in the binary the function is called from. No special instrumentation to use this technique.
