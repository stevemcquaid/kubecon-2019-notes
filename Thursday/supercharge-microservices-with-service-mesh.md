# Supercharge Your Microservices CI/CD with Service Mesh & K8s

*Speaker: Brian Redmond, Microsoft*

* Service Mesh could help with different rollouts
    * B/G - stand up then cutover
    * Canary - % rollover
    * A/B - mirror traffic to new -- difficult to replicate customer traffic for tests
* What are you looking for in a service mesh? 
    * gives uniform on a stack & decoupled from application code
* They use Flagger (open source)
    * helps with canary deploys w/service mesh and metrics
    * uses service mesh interface
* Service Mesh Interface
    * does traffic routing, telemetry, policy similar to ingress controller
    * makes it easy to swap out a service mesh underneath
* Performance testing is key

