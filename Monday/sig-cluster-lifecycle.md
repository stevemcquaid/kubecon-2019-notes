# Sig Cluster Lifecycle 
This is a moment for us to debate some high-level roadmap features that will impact how the community builds and runs Kubernetes.  It is also a good chance for folks to help shape the vision of what's to come.

Timothy St. Clair - Senior Staff Engineer, VMware

ClusterAPI - Aims to be abstraction around everything


## ClusterAPI
* etcdadm
* kubeadm
* cluster-addons
  
## image-stamper
* immutable vm image tool based on packr

## component config
Dont want CLI flags everywhere. This is a config of components of cluster as objects on cluster


## k8s cluster provisioners
e2e cluster provisioners that try to do everything and use one or more of these components

such as:
* kops
* kubespray

## Takeaways
* world keeps turning and we ened to turn with it
  * adapt to new inbound and challenge ideas
* config is hard, we are putting it off
* k8s config is awful, need ppl to help
* we need better e2e tests, automation reporting
* perf and ux matter a lot
* better docs and not be blocked
  * may federate out bulk of docs to repos
* need to help build out contributor base and find more scalable approached to managing things
  * needs more automation fairy dust

## Cluster Addons
Cluster addons is a CRD + controller based method to declaritively manage the lifecycle of core addon services to k8s

### Roadmap
* shared install primitive with kustomize
  * user-declared, config-driven
* build and use operators to manage addon logic
* want help * initial user feedback
* kubeadm integration
  * remove the hard coded addons
    * coredns
    * kube-proxy
  * support optional addons (install;upgrade CNI)
* kops integration
  * decouple long list of built-in addons
  * independant lifecycles from kubernetes
* support node local dns in kops & kubeadm

## Call to Action
* add-ons get an independent lifecycle
* leveraged across installers
* levels the playing field for "non-core" addons

# Ideas - could be punted to helm
* Ingress is a complex usecase with lots of implementations
* Metrics server
* Logging

### Discussion of helm vs addon-installer/operator

# kube-proxy why not helm?
* Needed for bootstrapping a cluster
* needing svc cidr

# ClusterAPI
The cluster API is a k8s project to bring declaritive, k9s-style apis to cluster creation, configuration and management

## Roadmap
* v1alpha3: control plane + upgrades, machine pool, e2e testing frameowkr, clusterctl v2, node remediation
* want to figure otu and optimize UX
  * have a clearly defiined contract to enable cross components behaviors
* get more feedback from the wild
  * defaults vs other providers and see where they are
* automate all the things (build, deploy, test, release)
* driving towards beta, or definition of beta
  * bnetter docs and explicit > implicit contracts
* adoption goals:
  * kops
  * use by azure
  * replace k8s/k8s/cluster folder
  * what would it take to get google to use?

## CTA
* kick tires, good, bad, ugly
* what are barriers to adoption? (why jsb, why?)
* enable a set of higher level tooling
  * multi-cluster tools, examples and insipre them
* alternative to cloud providers
  * build your own eks/gke/aks


# Image Builder
Roadmap:
* deduping the different approaches
* looping in common CI automation
* versioning
* try to dev `some form of` automation for a release


# kubeadm
is a node bootstrapper
something should provide the machines, then kubeadm creates k8s node on it
task if to setup a best-practice, conformant cluster

## lessons learned:
* ga is not end of journey, becuase the env around you is always changing
* being part of SCL is crucial to keep right direction
* getting robust E@E tests in place is hard (flakiness)
* housekeeping requires considerable effort ( reducsing deps tree)
* federation of component config has a lot of hidden implications
  * most probabaly, this discussion should be moved to a different level 
* after GA, it was more difficult to keep contribs engages and get new contribs, why?
  * activitices slow down vs Ga hype
  * focus on less fancy activities
  * GA constraints vs lower the bar for new contrib
* we should doubel down efforts for keeping healthier contrib base


## roadmap:
* simplify day 2 ops
  * from imperative to declarative - k8s operator
  * support new workflows: change the cluster, crt rotation, etc
* make kube adm more friendly for higher-level tools
  * allow easier vendoring
  * machine readable output
* increate flexibility around addons and etcd (addons prj and etcdadm integration)
  * opt-out default addons and optin to your custom addon list
  * lower down barrier between local etcd and external etcd
* simplify component config management
* move kubeadm out of the tree
  * build req automation and release

## CTA
the my dam team needs help

# Minikube
minkube is a local k8s cluster, opt for learning and app dev

## Draft roadmap
* focused on user-friendliness and perf
* vm-free deps with docker and podman
* multi-node
* decreased cpu overhead
* suspend & resume
* menubar UI + daemon for resource alters and cluster management
* richer addons functionality
* improved CNI support (weave, calico, flannel)
* planning for a post-libmachine world
* windows as a 1st class platform
* kernel-assisted mounts


# Kops

## roadmap 1.17
* cluster api support for nodes
  * why? cluster api promises better and more consistent control over machines
  * well start with nodes: (and tackle the rest of the control plane later)
* containerd support
  * why? dockers support timeline doesnt match with k8s, their build 
* more work on docs
* 
##  adopt cluster api in 1.18
  * support masters/clusters
  * why? tackling second half of cluster-api support

# etcdadm

## Roadmap
* define API types
* read config from file
  * integrate with clusterapi project
  * support external etcd usecase
  * work together with kubeadm
* implement basckup/restore functionality
  * Give an example of how to take periodic backups automatically using etcdadm
* implement self-driving functionality
* support etcd non-voting members intro in v3.4

## CTA:
* growing the contrib base, make it easier to contrib
* docs

# 