# Towards Continuous Computer Vision Model Improvement with Kubeflow:

*Speaker: Derek Hao Hu - Snapcaht*

* 3.5 Billion snaps created every day, 60,000 lenses created by community 
    * Your Model is only as good as your training set
* Why Kubeflow?
    * K8s Native
    * Avoid Vendor lockin
    * easy to share between workflows, specify workflow as code
    * GPU resources
    * Metric Visualization Support
* Pain Points: 
    * Lacking Artifact Caching
    * python decorator to get around it - not perfect
    * storage with minIO in a recent update
    * Typing in KFP Components lacking - not easy to know what each component expects
    * okay on small scale, becomes un manageable with large scale
    * work around is a shared "kfpschema" package, data typing info

