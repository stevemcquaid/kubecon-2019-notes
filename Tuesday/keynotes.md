# Keynotes

## CNCF
* New community - we are 5 yrs old
* Grow community

#### New gold and platinum members

#### CNCF Jobs Board
jobs.cncf.io

Kubernetescommunitydays.org

## Project Updates
* Bryan Liles - Sr Staff Eng VMWare

# CoreDNS
Graduated

# Vitess
Graduated

### Graduated CNCF Process
* Adoption
  * Mission critical in prod
* Maintainer diversity
* Project Health

### What is Vitess
Cloud Native DB
* run in k8s without losing data
* scale massively
* 5 9s avail
* based on mysql

### Case studies
* Slack
* JD.com
  * 35M peak QPS
  * 30k pods
  * 4000 keyspaces
* Nozzle
  * startup
  * all in k8s
  * move from cloud to cloud
* If youre moving to k8s, dont leave your data behind

### Dont miss talks
* building resilient systems - slack 1150
* stateless storage in the cloud - planet scale 320 (keynote presenter) - sigu?
* gone in 60 minutes - nozzle- thursday

# Linkerd
* Open source CNCF Service Mesh
* Linkerd talks from nordstrom, mc, paybase, buoyant

# Helm
* Helm 3 released

# Jaeger
* Graduated Status

# OPA - open policy agent
* torin sandall, styra
* general purpose policy agent
  * enforcement in the software services
  * policy into the opa engine
* declaritive policy language
  * rego - latin to rule
* library (go), sidecar/host-level daemon
* management apis for control and visibliity 
* tooling to build, test, and debug policies
* production users and metrics
* OPA decourples desicion making from enforecement
  * in k8s its usually admission control
  * envoy - external authz
* WASM (web assembly)
  * emerging as standard exec environment
* latest release of OPA (v0.15.1) compiles any Rego to Wasm
* blog.openpolicy.org

# Etcd
* latest release = 5k nodes clusters

# CloudEvents
* Achieved incubation status
* release 1.0
* is a spec for sending events
  * why?
  * Docs are important?

# Keep K8S Caffeinated
* Erin Boyd
  * Principlal soft eng, red hat
  * CNCF storage sig co lead
* Operator framework
  * rook
  * strimzi
    * kafka
  * noobaa
    * obj store?
  * kubevirt
    * vm on k8s
  * Single button automation
* Rook
  * minIO
  * cassandra
  * cockroach db
  * address complex of non-cloud storage on k8s
* disconnected storage in k8s
* process
  * select
  * deploy
  * integrate
  * consume
  * (next) scale
* multicsluter storage at scale is hard
  * migrate
  * snapshot
  * backup
  * cloning
  * data policy

# NATS
* Derek Collison
  * founder CEO Synadia
* NATS Project Update
* Connected Economy
* NATS.io
  * NATS is a simple cloud native proven messaging system
  * scalable services and streams
  * at most one and at least oce QOS
  * routing on subjects, topics
  * Lots of clients
  * lots of users
* use cases
  * cloud messaging
    * services
    * event data streaming 
    * c2c
  * iot and edge
    * telemetry, sensor, c2c
  * augmenting or replacing legacy messaging
* Usages
  * [Choria](https://choria.io/) - orchestration system
  * netlify
  * mastercard legacy transformation
  * storageos as a control plane
  * tinder - migrated from poll to push
  * platform9 - serverless - event sourcing
  * qlik - data analytics - broadcast messaging for quque, cache validation
* NATS Ecosystem
  * nats integrations
    * simple curl command to install and deploy to k8s
    * prom export, fluentd plugin, opentracing support
    * dapr.io coponent integration
    * spring boot starter
    * nats cloud stream binder for spring
    * nats kafa bridge
    * MQseries bridge
    * go-cloud go-micro bridging?
  * nats monitoring
    * supercluster metrics
    * extended superclusters
  * NATS getting started
    * basic messaging patterns
    * services - request/reply
      * scale up/down
      * 
    * streams - events and data
      * scalable N:M comm
      * realtime and persisted
      * playback by time, seq, all or only last
  * Accessing a NATASsystem
    * free comm servers
      * demo.nats.io
    * k8s
      * curl install
        * 3 node + metrics
    * docker
      * docker run nats:latest
    * additional info
      * docs.natios.io/nats-server/installation
  * HTTPS vs NATS(requestor)
    * nats.connect()
    * nc.Request()
  * service
    * nc.queueSubscribe("bar", "v0.1")
  * NATS service
    * deploy to any cloud, any geo, any deployment framework
    * on-prem, cloud edge or iot
    * no lb required
    * no dns updates to launch service
    * no config changes to scale up or down
    * transparent service latency tracking (3 points of reference)
  * history of nats
    * nats started a s a project to power cloudfoundry
    * c2c
    * querying
    * telemetry and events
    * location transparency
    * addressing and discovery
    * distr scheduler
    * highly resilent and self healing
  * nats "then"
    * built for me to serve cloud foundry & BOSH control planes and telemetry system
  * Nats "now"
    * be the enabling tech to connect everything
    * shared util of any size
    * decentralized and federated
      * mix a shared util with your own servers and security
    * secure by default, no ps or keys, powerful authz
    * on-prem: multi-cloud, multideployment, edge, iot
    * communicate, plublish, consume and save and restore state
    * healthy and thriving exocsystem of services and streams
  * Last 2.5 years
  * designed PLI/JWT security for authz and authn
  * no private keys trans or stored on any NATS servers
  * move to a secure multi-tenant distr design
  * additional network topo
    * gateways for global super clusters
    * leadnodes to extend a NATS system with your own servers and auth
    * dynamic
  * jetstream
    * moving into tech preview
    * nest gen persistent messaging
    * years in the design and iompl
    * built into every NATS server, works with all clients
    * supports streams, message queuq, work
    * push and pull modes for consumers
* whats next?
  * iot and edge
  * native mqtt support
  * websocket support for moile and web
  * WASM
    * secure ingress and egress filtering and customization
    * jetstream filters and processing
  * additional stateful service, k/v, etc
* learn more
  * deep dive on thursday
  * 1055 am room 6e thursday
  * slack channel

# Confidential computingi to K8S 
* Lachlan Evanson
  * principal pm azure
  * board member CNCF
* App security
  * concerns
  * Need hardware protected
* Layers of abstraction
  * gvisor
  * firecracker
* open enclave SDK
* confidentiail computing consortium
  * an effort to secure data in use
  * intel software gueo extension
* using open enclave sgx device plugin
  * `openenclave.io/sgx_epc_MiB: "82"` # encrypted memory
  * aka.ms/kubecon2019SD
* 