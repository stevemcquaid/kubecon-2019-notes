# Azure
Major bug fixes in v1.16
* disk attach/detach issues

## throttling - #247
* switting to list on vmss instead of GET on each VMSSVM
* change cache ttl from 1 to 10 min for VMSS and from 1 to 15 min for VMAS
* read from staled cache for certain LIST/GET

# How we test
* e2e test on a k8s cluster provided by aks-enginge
* testgrid.kis.io/provider-azure-on-call
  * run e2e periodically and on PR with cloud-provider-azure
  * run e2e on PR with k/k in -tree prov
  * run e2e periodically and on PR for k/k with windows nodes
  * run e2e periodically for k/k dualstack
  * run e2e periodically and on PR for azure disk CSI and in-tree drivers

Dualstack will be presented tomorrow at the keynote

# Plans
* Independent release and versioning with completion of out of tree provider
  * currently linked with in-tree release cycle becuase they are in-tree. breaking code out will help speed this up
* observability with opencensus/opentleemetry
* improved perf and reliaiablity thru:
  * k8s e2e tests as VMSS release gate + inscreated collab
  * common azure-core module shared with cluster-api-azure
  * enhanced perf and scalability testing
  * workdload scenario testing
* integrated cloud provider support for AzureStack Hub

ClusterAPI is emerging as a way to manage k8s on diff infra
* Increasingly invested in develeping clusterapi driver for azure
* Consolidate into common modules

# Get involved
slack: #provider-azure
deep dive wed 1050am 33ABC
meetings are posted on youtube
mondays 1st 630am and 3rd @ 5pm PT
https://zoom.us/j/586836662

