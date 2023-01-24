# route53 DNS Domain Delegation (including Cross Account)

This demonstrates a way that you can delegate DNS domain "management" to a "next level" domain.


| account  | domain                   |
|:--------:|:-------------------------|
| 234567   | clouditoutloud.com       |
| 987654   | myeks.clouditoutloud.com |
| 456456   | myocp.clouditoutloud.com |
(*) account numbers are faked, in case not obvious ;-)

## Scenario
I have several accounts that manage different parts of my workload.  In this case, accounts for either [AWS EKS](https://aws.amazon.com/eks/) or [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) (aka "ocp").  

Following the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected) I want to minimize blast radius by having resources managed by separate accounts. (i.e. if account 456456 gets comprimised, somehow, the damage/impact will be limited to that account only)

## Discussion Points
I am going to track some questions that might come up (and address them as I have time)

* why not just use [Resource Access Manager (RAM)](https://aws.amazon.com/ram/)?

## References
