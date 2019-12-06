### Keynote talks

- Ecosystem Optimizations
- Corporate Optimizations


Pentesting
k8s used to be able to have root commands run with an unauth curl

Community is great
Get up and running w/o having to run it "the hard way"

Conway's law - build software that reflects the organization

Diverse teams and diverse users. Bias.

Security implications of having a lot of trust.

Do you build for an assumption of a particular user? You need to design for all users.

Attackers have user stories

Who are attackers?
- In it for ideals
- because curious
- financially montivated
- governments


Who do attackers think?
- What do you look for if you're a k8s dev? operator? tester?
- builders vs. breakers
- `kubectl auth can-i --list --namespace=kube-system`
  - Allows a attacker to more easily
  - Ephemeral containers allow possibility. creative hacks that may be hard to detect


Designing for defense
- threat model - there is a book!
- what is in your graph? "defenders think of list and attackers think in graphs" describe things as a network, relations on things
- check your assumptions (k8s is secure by default -- it is not!)


Play goose.game to help think like an attacker.


#### Seamless Customer Experience powered by k8s @Edge

