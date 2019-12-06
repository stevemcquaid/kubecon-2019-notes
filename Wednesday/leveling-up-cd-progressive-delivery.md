# Leveling Up Your CD: Unlocking Progressive Delivery on K8s:

*Speaker: Daniel Thomson & Jesse Suen, Intuit*

* 1,300 deploys a day at Intuit
* Shorter does not mean safer
* What’s our contingency plan at MC? 
* Progressive Delivery = control over blast radius
    * Readiness probes are not enough for then, can halt a deploy, not rollback
* What are the dev use cases? 
* Used custom CRDs, service mesh, & ingress controls
    * If we used custom CRDs what would they look like? What do we need a MC that we don’t have already?
    * Analysis template CRD utilizes Kayenta with Spinnaker - is this something that could be useful for us in terms of measurements?
* Have a baseline to canary against

