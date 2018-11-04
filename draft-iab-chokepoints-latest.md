---
title: Internet Choke Points
docname: draft-iab-chokepoints-latest
date: 2018
category: info

ipr: trust200902
area: IAB
workgroup: IAB
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: M. Nottingham
    name: Mark Nottingham
    organization:
    email: mnot@mnot.net
    uri: https://www.mnot.net/
 -
    ins: B. Trammell
    name: Brian Trammell
    organization:
    email: ietf@trammell.ch


--- abstract

This memo discusses points of control on the Internet, or "choke points", that may have architectural impact.

--- middle


# Introduction

Recent events have caused concern about control of access to the Internet, leading one infrastructure company's CEO to reportedly assert:

> Literally, I woke up in a bad mood and decided someone shouldn’t be allowed on the Internet. No one should have that power.

In fact, the Internet is both architected and administered to preclude any one entity from having this power, through the careful management of “choke points” where such power could be exercised.


# Choke Points on the Internet

A large influence on the architecture of the Internet was [a need to survive nuclear attack](https://www.rand.org/content/dam/rand/pubs/papers/2008/P1995.pdf), so that loss of no one link or node would preclude communication. This extends not only to the physical links that make up the Internet (seen, for example, in the [duplication of submarine internet links](http://submarine-cable-map-2016.telegeography.com/)), but also to the various services that Internet access depends upon; for example, the operation of [multiple DNS root servers](http://root-servers.org/).

Avoiding choke points is both a design goal for both the protocols and the services that make network access and operations possible, as well as an assumption made by each layer and service about its dependencies. The resilience of the Internet depends on this assumption.

This extends to the entities that operate the Internet. For example, not only are there multiple DNS root servers, but we also assure that they are operated by a number of parties, many of whom compete against each other.

However, there are some cases when there is an unavoidable choke point. For example, as a central source of truth regarding naming, administration of the name space within the Domain Name System is a necessary choke point.

When an Internet choke point can't be avoided, we assure that it is administered by multiple parties with balanced interests, often referred to as the [Multi-Stakeholder Model](https://en.wikipedia.org/wiki/Multistakeholder_governance_model). In the case of the Domain Name System, oversight is performed by ICANN, a multi-stakeholder organisation.

Similarly, the specifications that describe the Internet and the Web form another potential choke point, since they mediate how most people use the Internet. For these, standardization is overseen by the World Wide Web consortium and the IETF, both of whom subscribe to [open standards principles](https://open-stand.org/infographic-the-benefits-of-open-standards/).

Together, these architectural principles and corresponding practices assure that no one person, business or government can control the entire Internet.

# Emerging Choke Points

In some cases, external factors encourage the formation of a new choke point despite the efforts
outlined above. For example, near-monopolies on “last-mile” Internet access in some jurisdictions have led to concerns about [network neutrality](http://www.internetsociety.org/net-neutrality), since they act as a choke point.

Content Delivery Networks (CDNs) are sometimes viewed as another emerging choke point, because they are seen as essential in mitigating Distributed Denial-of-Service (DDoS) attacks. While there appears to be a healthy market of CDNs (and similar services) and the costs of using one have been driven down considerably over the years, some suggest that there is a risk of a choke point forming -- as there is wherever a function is critical to the Internet’s operation.

When such a choke point forms, one possible way to counter its ill effects is regulation, either externally or within the Internet ecosystem (e.g., as ICANN does).  While it may be appropriate as a solution -- especially when a monopoly forms -- the effect of regulation on the architecture need to be evaluated carefully.

Historically, the Internet has worked best as a network-of-networks, where each has administrative control to make decisions about who is allowed to connect locally. Imposing external constraints on how networks select their members and who they communicate with could have far-reaching effects, especially since they are often already subject to a variety of local laws and regulations.

Ensuring that choke points don’t form is preferable to enshrining them, since they introduce not only points of control, but also increase the risk of failure in that component, concentrate the risk of security vulnerabilities there, and can ultimately limit the scale of the Internet.

Therefore, when there is risk of a choke point forming, we look for other mitigations before considering constraints on the behaviour of infrastructure providers. This might take place through encouraging more diversity at the potential choke point, technical measures that counteract its formation, or other means.


# Avoid Choke Points

As John Gilmore said, “the internet interprets censorship as damage and routes around it.” Censorship is a form of control that relies on having an opportunity to exercise control. Limiting the number of choke points and assuring that any unavoidable points are appropriately administered allows this valuable architectural property to persist.

At the same time, the Internet’s composition as a network of independent networks is valuable; imposing external controls on them is to be avoided. However, this does not mean that internet infrastructure providers are without guidance; we note that the UN’s [Guiding Principles on Business and Human Rights](http://www.ohchr.org/Documents/Publications/GuidingPrinciplesBusinessHR_EN.pdf) is an already-existing framework for businesses (including Internet infrastructure providers) to make such decisions within while still respecting human rights -- including the right to Internet access.


--- back
