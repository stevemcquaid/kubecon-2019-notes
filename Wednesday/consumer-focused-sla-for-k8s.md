# Implementing a Consumer Focused SLA for a Kubernetes Based PaaS:

*Speaker: Shrenik Dedhia, Box*

* What is our current K8s SLA at MC? 
* How to measure Platform Health:
    * Define what unavailable means to us.
        * no connections in 5 minutes? 10 minutes? what? 
    * % of 500’s from API
        * doesn’t account for scheduler, controller manager, data plane
    * They used an app for exercising the data plane as a test - reminds me a bit of spinnaker timebomb
        * useful, but not totally representative of customer load/data
* Use what K8s has to make your life easier (i.e. readiness/liveness probes, PDB, Rolling Updates) - we have some of this already
    * What would happen in all apps bursted simultaneously in our K8s ecosystem?
* They used what they called a Critical Replica Availability “CRA” 
    * targets high availability for services and data driven accountability for service owners
* What’s the worst state that one of our clusters could get in to? 
* Do we treat all application equally? Should we/does it make sense to? 
    * should we implement pod priority &/or preemption?
* Is there a way to expose some metrics outside of Prod? 
* What is one metric that would make sense as a tool for both dev teams as well as higher up the chain for VPs to measure success? 
* Do we have an application best practices/FAQ doc? 

