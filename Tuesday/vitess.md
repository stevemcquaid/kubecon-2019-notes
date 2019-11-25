# Vitess @ Slack
* Queries per day: 53+ billion
* Storage provisioned: 7.5+ PB
* Served by legacy infrastructure: ~60%
* Served by Vitess: ~40%
* Target: 70% served by Vitess by EOY

# Run on AWS
* fully on ec2
* eventually on k8s
* ASG for stateless components
* ephenermal NVMe

# Deployment
* Cell is a failure domain
* only cross cell boundary when talking to another master of a shard
* cannot run replicas in diff cells

# Old Deployment Arch
* Cell spanned AZ
* failure in one az would take down a region due to consul + masters
