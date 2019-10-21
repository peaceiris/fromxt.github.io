---
title: "Introduction to HTTP/3"
date: 2019-01-28T08:23:28+08:00
categories:
  - "computer"
tags:
  - "HTTP"
---

HTTP is the application protocol that powers the Web. It began life as the so-called HTTP/0.9 protocol in 1991, and by 1999 had evolved to HTTP/1.1, which was standardised within the IETF (Internet Engineering Task Force). HTTP/1.1 was good enough for a long time but the ever changing needs of the Web called for a better suited protocol, and HTTP/2 emerged in 2015. More recently it was announced that the IETF is intending to deliver a new version - HTTP/3. To some people this is a surprise and has caused a bit of confusion. If you don't track IETF work closely it might seem that HTTP/3 has come out of the blue. However,  we can trace its origins through a lineage of experiments and evolution of Web protocols; specifically the QUIC transport protocol.
<!--more-->
Before we dive deeper into HTTP/3, let’s have a quick look at the evolution of HTTP over the years in order to better understand why HTTP/3 is needed.
In HTTP/1.0 a new TCP connection is created for each request/response exchange between clients and servers, meaning that all requests incur a latency penalty as the TCP and TLS handshakes are completed before each request.
![http1](https://blog.cloudflare.com/content/images/2018/07/http-request-over-tcp-tls@2x.png)
Worse still, rather than sending all outstanding data as fast as possible once the connection is established, TCP enforces a warm-up period called “slow start”, which allows the TCP congestion control algorithm to determine the amount of data that can be in flight at any given moment before congestion on the network path occurs, and avoid flooding the network with packets it can’t handle. But because new connections have to go through the slow start process, they can’t use all of the network bandwidth available immediately.

HTTP/3 is the HTTP application mapping to the QUIC transport layer. This name was made official in the recent draft version 17 (draft-ietf-quic-http-17), which was proposed in late October 2018, with discussion and rough consensus being formed during the IETF 103 meeting in Bangkok in November. HTTP/3 was previously known as HTTP over QUIC, which itself was previously known as HTTP/2 over QUIC. Before that we had HTTP/2 over gQUIC, and way back we had SPDY over gQUIC. The fact of the matter, however, is that HTTP/3 is just a new HTTP syntax that works on IETF QUIC, a UDP-based multiplexed and secure transport.
![http3_1](https://blog.cloudflare.com/content/images/2018/07/http-request-over-quic@2x.png)
![http3_2](https://blog.cloudflare.com/content/images/2019/01/http3-stack.png)

Here are some references:

1. [HTTP/3: From root to tip](https://blog.cloudflare.com/http-3-from-root-to-tip/) - great article about the HTTP history

2. [HTTP/3 TALK ON VIDEO](https://daniel.haxx.se/blog/2019/01/23/http-3-talk-on-video/) - presented by by Daniel Stenberg

3. [HTTP/3 EXPLAINED](https://daniel.haxx.se/blog/2018/11/26/http3-explained/) -  describes what HTTP/3 and its underlying transport protocol QUIC are

4. [QUIC: A UDP-Based Multiplexed and Secure Transport](https://datatracker.ietf.org/doc/draft-ietf-quic-transport/)





