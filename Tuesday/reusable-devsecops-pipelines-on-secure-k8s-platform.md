# Building Reusable DevSecOps Pipelines on a Secure Kubernetes Platform:

*Speaker: Steven Terrana (Booz Allen) & Michael Ducy (Sysdig)*

* how to reduce time from Exploration discovery → Patching?
* Shift left security into the Dev Lifecycle more
    * making sure containers are compliant with security
* Developer need fast feedback loop
* Trusted Software Supply chain - unit, functional, browser based testing, etc
* CI/CD pipelines for multiple applications:
    * How to manage different tools for front end vs back end applications?
    * CI/CD out there is mostly targeted at applications
    * one pipeline per microservice.
* Every Dev team with a dev pipeline - build, package, scan, deploy, test
    * How to create a templated workflow that works for everyone, including security?
    * organizational goverance. standardize
* Falco - Open source solution for monitoring - detects suspicious behavior on containers based on rules set
    * makes anomaly detection easier
    * takes in system calls, k8s audit events, k8s metadata
    * event stream of all the calls happening in containerized workload, what processes are doing what, etc.
    * output API based on GRPC, expanding on outputs that are possible

