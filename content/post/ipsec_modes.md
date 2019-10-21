---
title: "IPSec Modes: Transport and Tunnel"
description: IPSec modes
date: 2018-12-05
categories:
  - "computer"
tags:
  - "computer"
  - "network"

---
IPSec modes are closely related to the function of the two core protocols, the Authentication Header (AH) and Encapsulating Security Payload (ESP). Both of these protocols provide protection by adding to a datagram a header (and possibly other fields) containing security information. The choice of mode does not affect the method by which each generates its header, but rather, changes what specific parts of the IP datagram are protected and how the headers are arranged to accomplish this. In essence, the mode really describes, not prescribes how AH or ESP do their thing. It is used as the basis for defining other constructs, such as security associations (SAs).

Let’s take a look at how the two modes work.

<!--more-->


## Transport Mode

As its name suggests, in transport mode, the protocol protects the message passed down to IP from the transport layer. The message is processed by AH/ESP and the appropriate header(s) added in front of the transport (UDP or TCP) header. The IP header is then added in front of that by IP.

Another way of looking at this is as follows. Normally the transport layer packages data for transmission and sends it to IP. From IP's perspective, this transport layer message is the payload of the IP datagram. When IPSec is used in transport mode, the IPSec header is applied only over this IP payload, not the IP header. The AH and/or ESP headers appears between the original, single IP header and the IP payload. This is illustrated in Figure 1.

![avatar](http://www.tcpipguide.com/free/diagrams/ipsectransport.png)


## Tunnel Mode

In this mode, IPSec is used to protect a complete encapsulated IP datagram after the IP header has already been applied to it. The IPSec headers appear in front of the original IP header, and then a new IP header is added in front of the IPSec header. That is to say, the entire original IP datagram is secured and then encapsulated within another IP datagram. This is shown in Figure 2.

![avatar](http://www.tcpipguide.com/free/diagrams/ipsectunnel.png)