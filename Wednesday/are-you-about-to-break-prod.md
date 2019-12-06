### Are you about to break prod

Experience testing enterprise software

Testing fundamentals
Unit vs. Acceptance testing (aka integration test, functional test)

Testing environments become a bottleneck for delivering software.

"Robust testing software" acceptance test _event-driven architectures?_

_Ephemeral Enviornment_ short lived environment. Only test microservice being looked at. Spin up extra pieces of infra to validate a single microservice.
Heavy leverage of open source
- k8s
- terraform
- ansible

Provision test env the same way as you provision prod env.

Templatize infrastructure.
Configure through environment variables.
Provision test specific infra.
Clean up resources at the end of every test run.

Trade offs
- Exact replica of prod
- Speed
  - New k8s cluster vs. pubsub topic
- Cost
  - single db instance for all tests
  - one replica for testing vs three in prod

Demo architecture
- demo-app k8s
- gcp bucket gcloud
- pubsub topic gcloud

Solid deployment strategy placed upfront. Pipeline?
GitLab CI for all pipelines
- Test and build
- Acceptance test
- pulumi preview (dry run of infra before provisioning)

Pulumi _create_ modern apps _deploy_ to any cloud _manage_ cloud environments.

"Everything we do is configuration driven"
