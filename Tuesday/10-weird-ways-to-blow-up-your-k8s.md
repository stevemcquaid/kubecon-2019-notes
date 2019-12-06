### 10 weird ways to blow up your k8s
### Melanie Cebula & Bruce Sherrod
Provide feedback through sched app to support talks you enjoy.

Tricks they've learned when doing k8s at scale. Challenges. Mistakes. Not all are great solutions

1. Zombie Jobs
k8s jobs and cronjobs.

When does a job/cronjob end? Could potentially run forever. `activeDealineSeconds`, `concurrencyPolicy`, `restartPolicy` must all be set. Marks job as failed if reach `activeDeadlineSeconds`

Use touchfiles, right? Well...

Github issue "better support for sidecar container..."

Introduce a run-sidecar container. Main container. Sidecar container. Touchfile. Need to support dumb init. Didn't work. Production incident.

"Whose PID is it anyways?" "Maybe working in the wrong abstraction layer"

"Maybe can solve in k8s" Attempt 3: solve it in k8s

Try 4: fork k8s. Bad idea
Try 5: solve in "patched" k8s. Apply patch to open source version of k8s. Found lyft patch.

Anootate containers as "Standard" or "Sidecar"

Takeaway: solve problem at appropriate abstraction level
2. Service Mesh Speeding Accidents
Service discovery called smartstack. Core: everypod has HAProxy sidecar container for outbound reverse proxy. HAProxy forks when updating HAProxy configuration. Tons of HAProxy may be cause outage. Just add a wait, right

`spec.strategy.rollingUpdate.maxSurge` 100%. If set this way, service mesh can't keep up.

`lifecycle.preStop.exec.command` = ['bin/sleep', 120]
`terminationGracePeriod`

Takeaway: k8s can cycle pods super fast, even if your service mesh can't keep up.

3. Monster Daemonsets
Download a huge amount of data every time initialize.

Daemonset is flakey.

Maybe instead of daemonset, do deploy with `podAffinity`.

Another idea: use daemonset and use taints & toleration. Maybe we can taint on pod readiness. Complexity wasn't worth it.

Daemonset. Daemonsets can easily take up too much space on your cluster. Can cause OOM issues, that could cause the cluster to go down.

Takeaway: Daemonsets can take down a cluster more easily than other deployment types
4. Make a lot of docker images
ECR has limit on amount of repos you can have. Lifecycle policies in AWS. No way of telling AWS not to delete current one.

ECR Cleaner. Runs once a day as cron job. For each ECR repo, delete down to some threshold but skip ones that are in use.

First issue: CI fails due to docker errors. Root cause: we were generating more images than the daily cron job. So, run cron job hourly. So far, holding up.
Second issue: rorating k8s minion node takes down services. "Find all images in use" Cron job only found images in the cluster it's running on, which deleted some images that were in use in other clusters. So where do you run ECR cleaner?

Needs to know about all images in all clusters. Speakers added new cluster, which has permission to access API for other clusters.

Takeaway: Make sure to keep track of all your docker images
5. To init or not to init, that is the question
Turn on/off features, adjust tests. Have runtime config agent.

Try 1: Split update logic into init container.
But, failed to connect to runtime: connection refused.
Try 2: Have init container set up it's own network proxy.
Try 3: make runtime config sidecars. Network proxy needs to be up before config agent. Race condition.
Try 4: Wait for network proxy script to wait for config agent.

Takeaway: You might need to support ordering between sidecars too!
6. Where's my custom resource?
CRDs are great! One challenge with CRDs is when deploys are completed. Utilize `status`, right?

When is custom resource deploy complete? Controller updates the resource when status is Ready or Error.

Only controllers can update `status`.

Hard to debug and hard to figure out what had happened.

`spec.metadata.generation` When you update resource, k8s will update `generation` automatically. Allows you to figure out whats happening to CRDs.

Controller adds `status.observedGeneration` so controller knows to apply or not.
Takeaway: knowing when deploy is complete is tricky
7. I can't believe I have all the node resources!
Large memory or cpu causes OOM. Older version of JDK aren't aware of Cgroups. Update java.

Not just specific to java resources. Envoy sets concurrency to # cpus on underlying host by default. Could cause contention on host!

Takeaway: Beware of language frameworks and sidecars
8. Autoscalacolypse

Autoscaling is great!

New resource called "Horizontal Pod Autoscaler" Keep utilization approximately flat.

Say service starts tons of CPU on initialization. Well...

Autoscaling not so great when CPU on init is high. Scales up. More pods in init w/ high CPU. Scales up. More pods in init w/ high CPU. Etc.

How do you fix this? Surely there is a setting. There used to be a setting from this. Removed a property.

Setting called `--horizontal-pod-autoscaler-sync-period=300s` hack. run the autoscaler once every 5 minutes. That way it reacts to real traffic spikes. Doesn't solve issue, just mitigate.

"Runaway autoscaling"

Takeaway: autoscaling doesn't work great for pods with high cpu usaged.
9. Hey, my scheduled upgrade caused k8s cluster to go down

k8s health checks
Readiness Probe: "Don't send traffic to me"

Health check for containers. What should health checks be?

Health checking is per container.

Don't set probes for non-critical containers. Just don't set the probes.

Crashing container fails readiness check.

Pod only received traffic if all containers are ready.
Soln: Some containers are more equal than others.
continue if container

Takeaway: be careful when configuring health for your pods.
10. Scheduling is easy and fun.

k8s scheduler is not good at AZ balancing. Actually quite bad. How solve?

Deployment pruner controller. Check for out of balance. Deletes pods. Fights with k8s scheduler. Process is slow to rebalance.

Stop-gap solution. Not good solution.

Sometimes you need to fix in k8s. Create patches. Some are still open (please help getting them merged!). Fix bug in AZ scheduler.

Do not need to fork *ahem* "patch"

Takeaway: you may need to make fixes to k8s scheduler itself.
