---
title: "EIP use cases"
#abbrev: "TODO - Abbreviation"
category: info

docname: draft-eip-use-cases-latest
#submissiontype: independent  # also: "independent", "IAB", or "IRTF", "IETF"
#consensus: true
#v: 3
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
    organization: Univ. of Rome Tor Vergata / CNIT
    email: "stefano.salsano@uniroma2.it"
 -
    name: "Hesham ElBakoury"
    organization: Consultant
    email: "helbakoury@gmail.com"

normative:

informative:
  draft-eip-headers-def:
    title: "Extensible In-band Processing Headers Definitions"
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

--- abstract

This document discussed use cases for the Extensible In-band Processing solution.

--- middle

# Introduction

EIP (Extensible In-band Processing) extends the functionality of IPv6 layer to support the requirements of future Internet services / 6G networks. In a nutshell, IPv6 nodes (routers and hosts) can read/write EIP information in packet headers to support different use cases.

EIP provides a common framework and solution which can be tailored for the different use cases. Each use case will have its own specific architectural aspects and protocol specifications.

In this document, a set of use cases for EIP is discussed. 

# Use cases

## Advanced monitoring

Traditional network monitoring solutions are based on the centralized collection of monitoring data collected by network nodes (SNMP/Netflow). These traditional solutions are "slow" and have scalability issues. They are not meant to monitor a large number of single flows in real time, they are meant to monitor large aggregates of flows (e.g. all traffic flowing on a given link). Typical time scale of the reaction time of the management system is in the order of minutes (e.g. 1-5 minutes).

The traditional approach separates the data plane and the management plane. The nodes collect counters and statistics, then they communicate with the NMS (Network Management Stations) over the management plane. 
Current technologies make it possible to define more complex monitoring operations to be performed by nodes in the data plane. The protocol extensibility offered by EIP is the natural complement to this new advanced monitoring approach. Thanks to information carried in the EIP header, it is possible to use the data plane also to synchronize monitoring operations across different nodes and it is possible to collect monitoring information in real time. Data plane entities can be used to sample and aggregate monitoring information. 

Different EIP Information Elements are described in [draft-eip-headers-def].




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
