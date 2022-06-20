---
title: "Extensible In-band Processing (EIP) Use Cases"
#abbrev: "TODO - Abbreviation"
category: info

docname: draft-eip-use-cases-latest
submissiontype: independent  # also: "independent", "IAB", or "IRTF", "IETF"
#consensus: true
#v: 3
# test {{I-D.draft-filsfils-spring-path-tracing}}
# The Internet Draft {{I-D.draft-farrel-irtf-introduction-to-semantic-routing}} provides a brief introduction to Semantic Routing. The Internet Draft {{I-D.draft-king-irtf-semantic-routing-survey}} includes a survey of several approaches for Semantic Routing.

ipr: trust200902
area: AREA
workgroup: SIG on EIP
keyword:
 - IPv6
 - Extension Headers
venue:
  group: EIP
  type: SIG
  mail: eip@cnit.it
  arch: http://postino.cnit.it/cgi-bin/mailman/private/eip/
  github: eip-home/use-cases
  latest: https://eip-home.github.io/use-cases/draft-eip-use-cases.html

author:
 -
    name: "Stefano Salsano"
    organization: "Univ. of Rome Tor Vergata / CNIT"
    email: "stefano.salsano@uniroma2.it"
 -
    name: "Hesham ElBakoury"
    organization: Consultant
    email: "helbakoury@gmail.com"
 -
    name: "Diego R. Lopez"
    ins: "D. Lopez"
    organization: "Telefonica, I+D"
    email: "diego.r.lopez@telefonica.com"

normative:

informative:
  I-D.draft-filsfils-spring-path-tracing:
  I-D.draft-farrel-irtf-introduction-to-semantic-routing:
  I-D.draft-king-irtf-semantic-routing-survey:
  id-eip-headers:
    title: "Extensible In-band Processing (EIP) Headers Definitions"
    author:
     -
        name: "Stefano Salsano"
        ins: "S. Salsano"
        organization: Univ. of Rome Tor Vergata / CNIT
        email: "stefano.salsano@uniroma2.it"
     -
        name: "Hesham ElBakoury"
        ins: "H. ElBakoury"
        organization: Consultant
        email: "helbakoury@gmail.com"
    date: 2022
    seriesInfo:
       Internet-Draft: draft-eip-headers-definitions
    format:
       TXT: "https://eip-home.github.io/eip-headers/draft-eip-headers-definitions.txt"
  id-eip-arch:
    title: "Extensible In-band Processing (EIP) Architecture and Framework"
    author:
     -
        name: "Stefano Salsano"
        ins: "S. Salsano"
        organization: Univ. of Rome Tor Vergata / CNIT
        email: "stefano.salsano@uniroma2.it"
     -
        name: "Hesham ElBakoury"
        ins: "H. ElBakoury"
        organization: Consultant
        email: "helbakoury@gmail.com"
    date: 2022
    seriesInfo:
       Internet-Draft: draft-eip-arch
    format:
       TXT: "https://eip-home.github.io/eip-arch/draft-eip-arch.txt"
  RFC8655:
  RFC8938:
  RFC8939:


--- abstract

This document discusses the use cases for the Extensible In-band Processing (EIP) solution.

Caveat: this document is still in brainstorming stage, it is distributed to stimulate discussion.

--- middle

# Introduction

EIP (Extensible In-band Processing) extends the functionality of IPv6 layer to support the requirements of future Internet services / 6G networks. In a nutshell, IPv6 nodes (routers and hosts) can read/write EIP information in packet headers to support different use cases.

EIP provides a common architectural and protocol framework which can be tailored for the different use cases. The EIP header includes a number of EIP Information Elements. Each use case will have its own specific architectural aspects and protocol specifications (EIP Information Elements).

In this document, some use cases for EIP are discussed. The EIP architecture is discussed in [id-eip-arch]. The EIP Information Elements are described in [id-eip-headers].

# Use cases (high level description)

## Advanced monitoring

Traditional network monitoring solutions are based on the centralized collection of monitoring data collected by network nodes (SNMP/Netflow). These traditional solutions are "slow" and have scalability issues. They are not meant to monitor a large number of single flows in real time, they are meant to monitor large aggregates of flows (e.g. all traffic flowing on a given link). Typical time scale of the reaction time of the management system is in the order of minutes (e.g. 1-5 minutes).

The traditional approach separates the data plane and the management plane. The nodes collect counters and statistics, then they communicate with the NMS (Network Management Stations) over the management plane.
Current technologies make it possible to define more complex monitoring operations to be performed by nodes in the data plane. The protocol extensibility offered by EIP is the natural complement to this new advanced monitoring approach. Thanks to information carried in the EIP header, it is possible to use the data plane also to synchronize monitoring operations across different nodes and it is possible to collect monitoring information in real time. Data plane entities can be used to sample and aggregate monitoring information.


## Semantic Routing

EIP can support Semantic Routing, when it is needed to place information in additional fields of the packets. Specific EIP Information Elements can be defined to carry the information needed by Semantic Routing.

A specific example is "geo-tagging", i.e. encoding the geographical position of a node in the IPv6 headers, so that this information can be used also for taking forwarding decisions.

## Deterministic Networking

[RFC8655] and [RFC8938] respectively specify the Architecture and data Plane Framework for Deterministic Networking. [RFC8939] specifies the IP data plane for DetNet, with this design choice: existing IP-layer and higher-layer protocol header information is used to support flow identification and DetNet service delivery. There are known limitations in the current IP data plane for DetNet, as discussed in [RFC8939]. In particular, the IP data plane for DetNet, uses 6-tuple-based flow identification, where "6-tuple" is destination address, source address, IP protocol, source port, destination port, and DSCP (optional matching on the IPv6 Flow Label field). Flow aggregation may be enabled via the use of wildcards, masks, lists, prefixes, and ranges. IP tunnels may also be used to support flow aggregation. The result of this design is:

* Operational complexity: from a practical standpoint, this means that all nodes along the end-to-end path of DetNet flows need to agree on what fields are used for flow identification. Possible consequences of not having such an agreement include some flows interfering with other flows, and the traffic treatment expected for a service not being provided.

* Lack of unified end-to-end sequencing information: service protection (if enabled) cannot be provided end to end, only within sub-networks.

EIP is used to add explicit DetNet information in IP packets. This simplifies the implementation of Deterministic Networking in IP routers and hosts and provides additional features with respect to current support of Detnet in IP networks.

EIP adds the support of explicit Detnet flow identification and sequencing information.

“Path Tracing” {{I-D.draft-filsfils-spring-path-tracing}}

## Slicing

TO BE PROVIDED

# Detailed design of EIP based implementation of the use cases

TO BE PROVIDED

# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
