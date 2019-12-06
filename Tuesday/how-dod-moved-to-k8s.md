### How DoD Moved to k8s and istio
### Nocolas Chaillan - Department of Defense

"This session will showcase the DoD enterprise DevSecOps initiative and it's architecture. It describes how the DoD is securing OCI compliant containers, moving to kubernetes and istio, ensuring abstraction and scale across hundreds of environments, including clouds, on-prem and classified environments."

"DevSecOps" - 16 month transformation

Question: who has put kubernetes on a plane, a fighter jet, or a ship?

Problem:
- Waterfall methodology, not agile
- 3-10 year software delivery cycle
- 3 month to 1 year
- Very manual (testing, security gates)
- Massive teams working on many products
- Time consuming process
- Scale

Layers built.
Integrated Defense Acquisition, Technology, and Logistics Life Cycle Management Framework

Must Rapidly adapt to challenges and work as a team. A large team. Various technologies. Bring it with you (even to space) with quite a few sensors and a lot of help all while building software innovations.

DoD enterprise DevSecOps initiative. Open source. Avoid vendor lock-in.

Whitelist access, blacklist access, which container can talk to which container. Knative to avoid any vendor lockin and bring everything with you.

Layers
- Application Layer
- Service Mesh Layer
- CI/CD layer
- platform layer
- infrastructure layer

Technology stack
- Plan & develop
- build
- test
- secure
- store artifacts
- deploy
- operate
- monitor
- scale

Technology
- Envoy
- Knative
- Elasticsearch
- Fluentd
- Kibana
- Twistlock - for continuous scanning, alerting, CVE scanning, behavior detection in dev and prod (build, registry, runtime)
- Anchoe

Goals
- Reduce attack surface
- hardening
- zero trust environment
- Automated STIG compliance with OpenSCAP

Tons of small clusters "at different specification levels"

They build cool f16 simulations! Help train pilots. Simulation is getting more and more realistic.

Can you put k8s in 45 days on the f16 jet.

Presentor shows video. SoniKube is the name of the team applying devsecops

Challenges have been around learning of k8s ecosystem. Grow in knowledge.

"Didn't have to change out the legacy hardware (!!!)"

DoD tests fighter jet software on cloud before uploading to the actual jet.

Future
- AI machine learning capability

"If k8s is good enough for DoD weapon systems, it is definitely good enough for your business!"

Q&A
Q: Do you have to comply with SOCKS for deploy?
Q: What is your support model?
A: FEDRAM is the abbreviation. Third party software must be run as a container. If it is in a container, then it can be accredited and run inside a k8s cluster.
"Cyber scanning tool", DoJ uses k8s too

Q: Where else are you running k8s for normal business operations for the airforce
A: Business systems are moving to cloud native, being split into microservices. AI machine learning
Q: High side, secure environments?
A: Yes. We have every layer

(High side?)

Q: Why choose istio and what are advantages? Why not other service meshes like linkerd
A: needed to start somewhere. Future plans on supporting multiple service mesh. Give it a shot and move fast, measure and test.

Q: Disconnected k8s - what is CI/CD pipeline? Describe?
A: Many is classified. Configuration is classified. Unclassified is the tooling. Same CI/CD pipeline.

Normal container pipeline. Package everything to upload to disconnected k8s cluster.

Q: After airforce contract, will you continue with airforce or continue work on disconnected k8s clusters?
A: Case by case program. No plan on switching until "we get to higher scale."

Q: How do you handle distributed decision making using k8s
A: Simple side: have systems where federated cluster (hard due to classified and reduce attack surface). Hardware disconnected requires redundant hardware.

Touch for me to answer question
Q: Do you have 3 concurrent k8s on a jet?
A: yes

Q: What was most challenging when
A: k8s isn't typically associated with disconnected hardware. Disconnected side would be very difficult if badly done.

Q: Fit for you - release process
A: Whole gated process, define steps. k8s "duty enterprise duty exercise design" phases/steps to become duty grade. This doc represents spec for MVP on duty grade. List of steps.

Q: What do you like about envoy. What changes would you like to see
A: Open source, high adoption, makes for a good bet. Good sign support will exist for a long time. UDP support. Gaps currently in UDP.

Q: Istio feature wish list
A: UDP support is a big one. More interaction with k8s and istio, having a "single pane of glass," works with knaitive. Ask my team!

Q: You rely heavy on open source. You customize some. Do you contribute back?
A: Yes, we go through our partners like Red Hat to contribute back to open source. Goal is not to fork software

Q: You doing gaming software? ;)
A: No :)

Q: How are you going to expand in airforce? What is point of convergence on single approach (e.g. kesselrun)
A: We've worked with kesselrun. Now working with multiple services, not just airforce. Ability to spin up DevSecOps quickly.

Full brief in repo!

Q: Cloud native. What sort of process and people challenges have you had to adapt to?
A: Culture shift. Training. Proposed value of tech. Locked in to tools. Important to work with open source (to avoid XP situation for example).

Q: How are you packaging scanning?
A: Helm, operators,
Q: Runs as sidecar?
A: Depends on the tool. Envoy is a sidecar

Q: No document on running on AWS govcloud
A: We do have documentation on AWS govcloud.

Q: Enterprise struggling at open source products, especially regulated environment like finance. What is your process to adopting open source software? Any program in place to contribute back to open source tools that vetted by DoD?
A: Give back to community is the open source repo they've put together.
