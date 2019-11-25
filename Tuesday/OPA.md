# OPA


## OPA - what is it?
* Rego - policy language
  * Go
* OPA has http svc
* embedded in go
  * sidecar hosr-level daemon
* wasm integration
* Rego playground

## OPA policy engine
* inputs and output are both json
* enforcement decoupled from decision-making
* input can be ANY json
* output can be ANY json

# OPA example use-cases
* admission ocntrol
* api authZ
* ssh sudo
* data protection
* data filtering

# OPA New & Trending use-cases
* CI/CD pipelines
  * spinnaker
  * boomerang
  * terraform
* public cloud object storage for bundles
  * s3
  * gcs
  * oci
* OPA Integration index
  * bit.ly/32pPWEI
* OPA use-case: k8s admission controller

# Gatekeeper
  * customizable k8s admission webhook that hekps enforce policies and strengthen governance
## motivations
* control what end-users can do
* ensure clusters are in conformance to policies
* preview the effect of policy changes in prod clusters to prevent impacts on existing workloads
* how do we help ensure conformance without sacrificing agility and autonomy?

# how we got here?
* MS = v2 = k8s policy controller (kpc) donation
* v3 released (constraint framework = CRD vs configmaps)

# Gatekeeper: v3
* OPA = policy agent
* data is replicated into OPA from gatekeeper
* policy templates 
  * function where you write the rules (REGO)
  * what kind of rules should the policy institute
* policy instances
  * caller to the function with all the params

# v1-v3
* v1 configmap -> v3 CRDs
* v3 has audit and dry run
  
# Gatekeeper - core features
* Validating admission control
  * Control what end-users can do on the cluster
* Context-aware/referential policies
* Constraints are parameterized and easily configurable by admins
* ConstraintTemplates provide the source code for constraints
  * Easily shared
  * Testable
  * Developed internally or sourced from the community
    * reference - folder in github
    * eventually popular policies in a repository/registry
* Audit
  * Periodically evaluates resources against constraints
  * Allows for ongoing monitoring of cluster state to aid in detection and remediation of pre-existing misconfigurations

# Gatekeeper: Latest Updates
* Dry run
  * Test canary releases in a cluster in stages without impacting the cluster and your users
  * Gain confidence for our policies for admins before enforcing them; gradual rollout
* Namespace Selector
  * Narrow the scope of resources a constraint can enforce to certain namespaces only
* Policy library
  * Community developed policies
  * Alternative to Pod security policies
* Multi-source constraint template
* Metrics

# Demo - Agile Bank goverance Policies
* All namespaces must have a label that lists a point-of-contact
* All pods must have an upper bound for resource usage
* All images must be from an approved repository
* Services must all have globally unique selectors
* Ingresses must all have globally unique hostnames

How to gain confidence for policies before encoring them
Gradual rollout

# DEMO
