# The Gotchas of Zero-Downtime Traffic w/K8s

*Speaker: Leigh Capili, Weaveworks*

1. If using a shell invoke explicitly
2. STOPSIGNAL overwrite SIGTERM
3. if have defaults unready = unalive live > ready
    * careful with timeouts on liveliness probe
4. Node Router & Ingress Controller
    * Careful with stop receiving connections vs. stop draining connections
    * can sleep in prestop to drain connections 
5. Deployments
    * rollingUpdate maxUnavilable 
    * audit repos - apps/v1 API used to default to 1
6. minReadySeconds & progressDeadlineSeconds 
    * keep app warm during update
    * if have capacity can speed up
    * maxSurge
    * What happens if we hit capacity? 
7. mismatched sig lifecycle w/side cars
    * make sure synchronized / scheduled 
    * use sleep longer on the sidecar 
    * Do we make sure sidecars are coming up when they should?

