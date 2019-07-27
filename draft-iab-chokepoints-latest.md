---
title: Internet Choke Points
docname: draft-iab-chokepoints-latest
date: 
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
    uri: https://trammell.ch


--- abstract

This memo discusses "choke points" in the Internet architecture and the
governance structures surrounding it. A choke point occurs where one single
entity or a small number of entities have the ability to make decisions with
wide-ranging or global impact some aspect of the use of the Internet. It
explores the implications these choke points have on the health of the Internet
as a global communications infrastructure, and provides guidance for avoiding
the creation of future choke points.

--- middle


# Introduction

[EDITOR'S NOTE: bring this up to date. keep the quote below but be a bit more Ripped From Today's Headlines ]

Recent events have caused concern about control of access to the Internet, leading one infrastructure company's CEO to reportedly assert:

> Literally, I woke up in a bad mood and decided someone shouldn’t be allowed on the Internet. No one should have that power.

In fact, the Internet is both architected and administered to preclude any one entity from having this power, through the careful management of “choke points” where such power could be exercised.


# Choke Points on the Internet

A large influence on the architecture of the Internet was [a need to survive nuclear attack](https://www.rand.org/content/dam/rand/pubs/papers/2008/P1995.pdf), so that loss of no one link or node would preclude communication overall. Although in some places Internet access is at risk -- especially when there is not adequate diversity of access available -- the Internet as a whole has proven resilient in the face of such physical disruptions. 

This desire for resilience is reflected in the modern Internet through measures like the [duplication of submarine internet links](https://submarine-cable-map-2018.telegeography.com). 

However, it is not limited to the physical components of the Internet; it also extends to the various services that Internet access depends upon, and the protocols that it uses. For example, there are [multiple DNS root servers](http://root-servers.org/), operated by a number of parties.

When any one component -- through its design or the constraints upon its use -- has the ability to deny access to the Internet (accidentally or not) or control its use, we call this a choke point. 

Avoiding choke points is both a design goal for both the protocols and the services that make network access and operations possible, as well as an assumption made by each layer and service about its dependencies. The resilience and long-term health of the Internet depends on this assumption.

This does not mean that we can prevent all possible choke points; if a node has only one connection to the Internet, that link will be able to deny access no matter what measures we take. Instead, our aim is to avoid unnecessary choke points, especially when they can influence large portions of the Internet.

## More than Resilience

As John Gilmore said, “the internet interprets censorship as damage and routes around it.” Censorship and other forms of control relies on having an opportunity to exercise that control. Limiting the number of choke points and assuring that any unavoidable points are appropriately administered allows this valuable architectural property to persist.

This emergent property of the Internet has proven to be one of its core features. By providing resilient communication, it also provides [EDITOR'S NOTE: missing sentence end]

At the same time, the Internet’s composition as a network of independent networks is valuable; imposing unnecessary constraints upon them is to be avoided. However, this does not mean that internet infrastructure providers are without guidance; in particular we note that the UN’s [Guiding Principles on Business and Human Rights](http://www.ohchr.org/Documents/Publications/GuidingPrinciplesBusinessHR_EN.pdf) is an already-existing framework for businesses (including Internet infrastructure providers) to make such decisions within while still respecting human rights -- including the right to Internet access.


# Identifying Potential Choke Points

[EDITOR'S NOTE: IMO (brian) this is more useful if split by why the choke point emerges, not past/future. Not sure the list of subsections below is exhaustive.]

## Physical Infrastructure

[EDITOR'S NOTE: usually a local problem: if there is only one access provider in a given area, that access provider is the Internet choke point from the point of view of users in the area.  Note that physical monopolies are the focus of the network neutrality debate in some jurisdictions.]

## Protocol Bootstrapping

[EDITOR'S NOTE: some chokepoints emerge because a protocol is designed to point to some piece of infrastructure to start itself up. Question: does the DoH case fit here?]

- DNS root servers
- others?

## Roots of Trust

[EDITOR'S NOTE: everything below needs citations.]

Asymmertric-key cryptographic protection of the security properties of protocols
using requires a method to define and agree upon the roots of trust for the
public-key infrastucture (PKI) associated with the protocol. Sometimes, there is
a single global root, as in the case with the Root Key Signing Key (KSK) in
DNSSEC. Sometimes, roots of trust are regionally distributed, as is the case
with the routing public-key infrastructure (RPKI), with one root per Regional
Internet Registry (RIR). Still other PKIs have arbitrarily many trust roots: in
the case of the Web PKI, each Certificate Authority has its own root,
individually trusted on a per-browser or per-platform basis.

Each trust root is associated with a governance structure to ensure proper
oversight over control of the root. For example, the DNSSEC root is administered
according to ICANN's policy process, the RPKI by each RIR's policy process, and
the Web PKI by the CA/Browser Forum.

Creating a new PKI for a protocol unavoidably creates a new chokepoint for the
protocol covered by the PKI, represented by the PKI's root, and requires the
creation of a new governance  However, reusing an existing PKI for a new related
protocol creates a dependency between policies covering the new protocol and
those covering the existing protocol, which may or may not be appropriate.

# Techniques for Managing Potential Choke Points 

There are some cases when there is an unavoidable choke point. For example, as the source of truth regarding naming, administration of domain names is currently a necessary choke point in the Internet architecture.

## Avoiding Choke Points

A choke point can often be avoided through good protocol design. 

- distributed
- avoid discriminators
- avoid adding new roles

## Balancing Interests

- create balanced markets
- standards
- federated systems

For example, Content Delivery Networks (CDNs) are sometimes viewed as another emerging choke point, because they are seen as essential in mitigating Distributed Denial-of-Service (DDoS) attacks. While there appears to be a healthy market of CDNs (and similar services) and the costs of using one have been driven down considerably over the years, some suggest that there is a risk of a choke point forming -- as there is wherever a function is critical to the Internet’s operation.

## Multi-Stakeholder Administration

Another technique for mitigating an unavoidable choke point is through formal delegation of its administration to multiple parties with balanced interests, often referred to as the [Multi-Stakeholder Model](https://en.wikipedia.org/wiki/Multistakeholder_governance_model). 

For example, in the case of domain names such oversight is performed by ICANN, a multi-stakeholder organisation.

Similarly, the specifications that describe the Internet and the Web form another potential choke point, since they mediate how most people use the Internet. For these, standardization is overseen by the World Wide Web consortium and the IETF, both of whom subscribe to [open standards principles](https://open-stand.org/infographic-the-benefits-of-open-standards/).

Together, these architectural principles and corresponding practices assure that no one person, business or government can control the entire Internet.

## Plausible Replaciblilty

[EDITOR'S NOTE: discuss the case of "big red buttons": if it is impossible to avoid a choke point in the architecture such as a single trust root, design the governance around the choke point such that (1) governance is split from execution and (2) execution can be switched to another entity. This option should be designed in such a way that the disruption caused by exercising it would be small enough to make the threat plausible.]

## External Regulation

Another possible way to counter the ill effects of a choke point is through legal means, for example regulation.  While it may be appropriate as a solution -- especially when a monopoly forms -- the effect of regulation on the architecture need to be evaluated carefully.

For example, near-monopolies on “last-mile” Internet access in some jurisdictions have led to concerns about [network neutrality](http://www.internetsociety.org/net-neutrality), since they act as a choke point.

Historically, the Internet has worked best as a network-of-networks, where each has administrative control to make decisions about local connectivity. Imposing external constraints on how networks select their members and who they communicate with could have far-reaching effects, especially since they are often already subject to a variety of local laws and regulations.

Ensuring that choke points don’t form is preferable to enshrining them in regulation, since they introduce not only points of control, but also increase the risk of failure in that component, concentrate the risk of security vulnerabilities there, and can ultimately limit the scale of the Internet.

Therefore, when there is risk of a choke point forming, we look for other mitigations before considering constraints on the behaviour of infrastructure providers. This might take place through encouraging more diversity at the potential choke point, technical measures that counteract its formation, or other means.



--- back
