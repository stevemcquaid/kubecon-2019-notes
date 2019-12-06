### ${Talk Name}
### ${Talk Author}

Where do I find plugins for kubectl?
- github?
- some list?
- package manager?


`krew` is a plugin manager for `kubectl`

- Functionality
  - discover
  - install
  - update
  - remove
- Started in 2018 as an intern project at gcloud
- Donated to k8s project in may 2019
- Not an actual package manager because it doesn't handle dependencies


"Glorified bash script"
kubectl plugins - 62

`krew` installs binary to `~/.krew`

Plugin manager vs package manager
- `krew` is a plugin manager


Kubectl plugins
Scheduler extension/custom scheduler
API access extensions
Custom resources
Custom controllers
network plugins
storage plugins

kubernetes core runs too slow

How to write a plugin
Let's write a plugin

SIG-CLI
