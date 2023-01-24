# route53 DNS Domain Delegation (including Cross Account)

This repo demonstrates a way that you can delegate DNS domain "management" to a "next level" domain.

You can see my [KnowBetterCloud - DNS Delegation Demo - using AWS route53](https://www.youtube.com/watch?v=3cuZfLxj5j0) | YouTube Video

| account  | domain                   | Level |
|:--------:|:-------------------------|:-------------|
| 234567   | clouditoutloud.com       | Second Level |
| 987654   | myeks.clouditoutloud.com | Third Level  |
| 456456   | myocp.clouditoutloud.com | Third Level  |

(*) account numbers are faked, in case not obvious ;-)

## Scenario
I have several accounts that manage different parts of my work.  In this case, accounts for either [AWS EKS](https://aws.amazon.com/eks/) or [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift) (aka "ocp").  
Following the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected) I want to minimize blast radius by having resources managed by separate accounts. (i.e. if account 456456 gets comprimised, somehow, the damage/impact will be limited to that account only)  

## How is this useful, or needed?
Here are a few discussion points where I have found DNS delegation useful.

### OpenShift  
Additionally, OpenShift has a dependency (requirement?) for a specific DNS configuration.
*  api.(OCP_CLUSTER_NAME).(OCP_DOMAIN_NAME)
*  *.apps.(OCP_CLUSTER_NAME).(OCP_DOMAIN_NAME)

Over the past 7 years, I had partnered with a number of customers to assist them in implementing Red Hat OpenShift (either to just "kick the tires" or production) - and each time there was lengthy and involved discussions (as there should be, I might add) about that requirement for OpenShift to have endpoints described above).  The easiest solution, that we had found, was to simply provide the group with their own third-level (or, sometimes fourth/fifth/etc...) domain.

### Let's Encrypt
There are several ways to create/manage certs, one of which is [Let's Encrypt](https://letsencrypt.org/getting-started/) and with Let's Encrypt, there are numerous ways to interact (manual, Certbot acme.sh, cert-manager, etc...)

One advantage I appreciate using these delegated domains is that I can manage my certificates for my "sub-domain" (third-level) independent of the second-level domain"

## Discussion Points
I am going to track some questions that might come up (and address them as I have time)

* Should all DNS be managed by the "parent account" and "second-level domain" owner?
* why not just use [Resource Access Manager (RAM)](https://aws.amazon.com/ram/)?

## References
