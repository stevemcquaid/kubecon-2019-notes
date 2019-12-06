### CNCF Project Updates
### Bryan Liles

(notes from previous 'sections' lost in an accident :( )

#### Open Policy A (OPA)
Production Users & metrics
- Pinterest
- Atlassian
- Capital One
- TripAdvisor
- Fugue
- Chef

OPA decouples _decision-making_ from _enforcement_. Webassembly emerging as standard execution environment.
Latest OPA compiles any Rego to WASM

#### ETCD
Etcd release over a month ago has been able to scale up to 5000 node clusters.

#### CloudEvent
Achieved incubation status
Released 1.0
_Specification for sending events_

### End CNCF Project Update

### Rook.io
Coffee is in our _DNA_
But it's a _process_ (to turn an observation of goat being more energetic to a normal `coffee`)

Operator (Strimzi, Noobaa, Kubevirt)

Single Button Automation
Foam, Milk, Espresso, Upgrade

Rook provides orchectration for volume management. Ceph.
Volumes may be stored in different clouds, and/or on-prem. "Rook/Ceph is like having the same type of coffee at home as in starbucks"

Select, Deploy, Integrate, Consume.... And now, Scale. Scale == Hard
- Migrate
- Snapshot
- Backup
- Cloning
- Data policy

Storage is critical to hybrid clouds.

### Derek, creator of Maps and Open(something)
NATS Project Update
Derek Collision
Cloud vs Data economy. What are we extracting out of a system. "We are actually in the connector economy"

Services, streams, 30 client implementations. NATS likes all the client implementations -- choose your own language!

Use cases
- Cloud messaging
  - Services
  - Event/data streaming
  - command and control
- IOT and edge
- Augmenting and replacing legacy messaging

User Testimonials
- Choria
- Netlify
- Mastercard
- Tinder - migrated from poll based to event based
- Platform9 - framework for "serverless"
- Qlik

NATS Ecosystem
NATS integrations
- simple curl command to install and deploy into k8s
- prometheus exports, fluentd plugin, opentracing/jaeger support
- Dapr.io component integation
- Spring boot starter

NATS Monitoring
- "We want to be able to observe apps running on NATS."
- Now, there is NATS global dashboard. SuperCluster metrics. Service latency - Global View (community request). Latency of request. How far away is user.

NATS getting started
Basic Messaging patterns. Services (request/reply). Streams (events and data)

Accessing a NATS system
- Free community servers
- k8s - now with single script to install NATS!
- docker - can run NATS inside single docker container
- additional info

HTTP vs NATS (Requestor) (Service)

History of NATS
NATS started as a project to power CloudFoundry
- Command and control
- querying
- telemetry and events
- location transparency
- addressing and discovery
- distributed scheduler
- highly resilient

NATS "then"
"Built for me" to serve _CloudFoundry_ and _BOSH_ control planes and telemetry system.

Be the _enabling_ technology to securely connect ALL the world's digital systems, services, and devices.

Connect Everything
- Shared utility of any size
- Decentralized and federated (mix a shared utility with your own servers and security)
- secure by default, no passwords or keys, powerful authorization
- on-prem, multi-cloud, multi-deployment, the edge, and IOT
- communicate, publish, consume, and save and restore state
- healhty and thriving ecosystem of services and streams

NATS Community
'The community is great. Keep contributing!' _and then he reads off stats of NATS github_

Last 2.5 years
- Designing PKI/JWT security for AuthZ and AuthN (w/ instant revocation)
-   NO private keys transmitted or store on any NATS server
- Move to a secure multi-tenant distributed design
- Additional network topologies

JetStream
"Next generation persistent messaging system"

What's next?
- IoT and edge - next thing for us
- Native MQTT support
- websocket support for mobile and web
- WASM support
  - Secure ingress and egress filtering and customization
  - jetstream filters and processing
- Additional stateful services, K/V, etc.

### Lockland Container ... Azure ... TOC contributor
Lachlan Evenson - Pricipal program manager, azure container computer board member, ...
Bringing confidential computing to k8s.

Application security
Concerns
- Data leaks
- unauthorized data access
- infrastructure confidence
- regulatory compliance

Layers of abstraction
- Container
  - Application
- Operating system
- Hypervisor
- Hardware

There is a need for hardware security. Confidential computing. Trusted execution environments. Open Enclave SDK. Isolated by the hardware itself. "Encryption down to the chip"

Scenario
- Securing LOB workloads
- Targeted benefits
- reducing the need for trust
- multi-tenant ML

Confidential computing consortium
