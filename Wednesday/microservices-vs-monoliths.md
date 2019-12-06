### ${Talk Name}
### ${Talk Author}

Microservces vs monoliths
trade offs between the two. "Mono-microlith" (lol).

Why monoliths are the greatest thing ever
- Monorepo
  - Website
  - Backend
  - one server
  - pingdom
  - nagios

And then things got more complicated...
Deployment at scale. Ansible. Trouble maintaining ansible playbook. Debug took resources. Sticky sessions for parallel scaling because app wasn't built for statelessness.

Internet says to move to microservices. 2015 microservice interest just starting to take off.

Why microservice? Scale. Scale duh. Horizontal scale vs vertical scale. More instances. Bigger instances. Scale throughput. Scale in organization.

Tons of teams working on same codebase. Release every week. One microservice for each team.

Worked until... It got out of hand. Distributed tracing. Temptation to go back to monolith.

"Monomicroliths" microservices in a monorepo. Might increase adoption since it's simplicity.

Modular codebase.
- Read
- write
- calculate
- process

gRPC interface. Contract. Interface. Idea is ease of use, so its okay if process is serializing/deserializing.

Write your own interface and use third parties through that interface. "Abstract your third parties." Allows you to stub out the third party services and "test your app in airplane mode, w/o the internet."

"I miss some things from the monolith world" It may take many microservices to create the setup that a monorepo provides.

"Monorepo all the things"

Effort to refactor codebase when all microservices are in their own repo.

Microservices are where we want to be, but keeping them in a monorepo also has advantages.

So, microservices vs monolith. Why not both? Monomicroliths.

Onboarding new developers benefits from this setup.

Q: How big are the teams? Disciplined engineers?
A: If code is modular enough and your teams are disciplined then you don't reap as many benefits. Super small teams.

"Artificial forced boundaries" so devs don't cheat.

