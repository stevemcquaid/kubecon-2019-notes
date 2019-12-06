# Developer Experience on CD: Build a CD Platform to K8s that Developers Love:

*Speaker: Euccas Chen & Tobi Ogunnaike, Pinterest*

* Again custom CRDs and integrating custom infrastructure and controllers
* Use their own Teletraan Deploy tool — open source
* Problems Come Across:
    * Complexity - Don’t expect devs to know the details
    * Operational - too many tools/hoops to jump through
    * Specific to them - heavily invested in internal tools how to break from? 
* Goals they set: --- What are our goals for K8s?
    * Simple - one interface, abstract
    * End-to-End - commit, deploy, & debug
    * Customize & Pipelines
* Built Hermez internally: 
    * User facing CD system
    * “K8s first”
    * Used Orca microservice from spinnaker to orchestrate
* Overall: Don’t think we’d do something like Hermez but things to think about:
    * What’s our scope of K8s? 
    * Who are our users and what is their feeback?
    * Demos / Brownbag sessions may help with onboarding woes. - SFCD has started to do some brownbags on different tools. 

