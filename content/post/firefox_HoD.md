---
title: "Configure DNS Over HTTPS and ESNI in Firefox"
date: 2019-01-31T12:09:33+08:00
draft: true
categories:
  - "computer"
tags:
  - "HoD"
  - "Firefox"
---

DNS over HTTPS is a relatively new feature to improve the privacy, security and connection reliability of DNS look-ups; the feature is currently in draft status and tested by companies such as Google, Cloudflare or Mozilla. Firefox  now supports encrypting the TLS Server Name Indication (SNI) extension, which helps prevent attackers on your network from learning your browsing history. You can enable encrypted SNI today and it will automatically work with any site that supports it. Currently, that means any site hosted by Cloudflare, but we’re hoping other providers will add ESNI support soon.
<!--more-->

Firefox users can try out this enhancing feature now by performing the following steps:

1. Type about:config in the location bar

2. Search for network.trr (TRR stands for Trusted Recursive Resolver – it is the DoH Endpoint used by Firefox.)

3. Change network.trr.mode to 2 to enable DoH. This will try and use DoH but will fallback to insecure DNS under some circumstances like captive portals.  (Use mode 5 to disable DoH under all circumstances.)

4. Set network.trr.uri to your DoH server. Cloudflare’s is [https://mozilla.cloudflare-dns.com/dns-query](https://mozilla.cloudflare-dns.com/dns-query) but you can use any DoH compliant endpoint.

5. Search for network.security.esni.enabled and set it to ture.

![HoD1](https://i1.wp.com/hieloz.files.wordpress.com/2019/02/1.jpg)

![HoD2](https://i0.wp.com/hieloz.files.wordpress.com/2019/02/2.jpg)

**Test results:**

![HoD3](https://i2.wp.com/hieloz.files.wordpress.com/2019/02/3.jpg)


Once you’ve done that, this should automatically enable ESNI for any site that supports it. Right now, that’s just Cloudflare, which has enabled ESNI for all its customers, but we’re hoping that other providers will follow them. You can go to: [https://www.cloudflare.com/ssl/encrypted-sni/](https://www.cloudflare.com/ssl/encrypted-sni/) to check for yourself that it’s working.

Reference:

1. https://blog.mozilla.org/security/2018/10/18/encrypted-sni-comes-to-firefox-nightly/

2. https://blog.cloudflare.com/encrypt-that-sni-firefox-edition/

3. https://www.mozilla.org/en-US/firefox/channel/desktop/#desktop-nightly-download

4. https://www.cloudflare.com/ssl/encrypted-sni/

5. https://blog.mozilla.org/security/2018/08/13/tls-1-3-published-in-firefox-today/

6. https://blog.nightly.mozilla.org/2018/06/01/improving-dns-privacy-in-firefox/

7. https://hacks.mozilla.org/2018/05/a-cartoon-intro-to-dns-over-https/

8. https://github.com/googlehosts/hosts/issues/87
