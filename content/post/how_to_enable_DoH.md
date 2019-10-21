---
title: "How to enable DNS-over-HTTPS (DoH)"
date: 2019-09-09T07:35:15+08:00
categories:
  - "computer"
tags:
  - "Chrome"
  - "FireFox"
  - "DoH"
---

![05_01.png](https://2r4s9p1yi1fa2jd7j43zph8r-wpengine.netdna-ssl.com/files/2018/05/05_01.png)

<!--more-->

## What is DoH
DoH [IETF RFC8484](https://tools.ietf.org/html/rfc8484) allows browser to send DNS requests as normal-looking HTTPS traffic to special DoH-compatible DNS servers (called DoH resolvers). Basically, it hides DNS requests inside the normal deluge of HTTPS data. DoH doesn't encrypt DNS requests. That's a different protocol, namely DNS-over-TLS, aka [DoT](https://gamedun.github.io/-----https://en.wikipedia.org/wiki/DNS_over_TLS).

By moving DNS server settings from the OS to the browser level, and by encrypting the DNS traffic, DoH effectively hides DNS traffic from internet service providers (ISPs), local parental control software, antivirus software, enterprise firewalls and traffic filters, and about any other third-party that tries to intercept and sniff a user's traffic.

Mozilla has already rolled out support for the DoH protocol a few years back. Currently, enabling DoH support in Firefox is as easy as pushing a few buttons. 

On the other hand, enabling DoH in Chrome isn't as easy, as Google is currently a little bit behind with supporting the protocol. DoH works just fine in Chrome, but there's no user interface for enabling or configuring it.

## Enabling and disabling DNS-over-HTTPS in Chrome

To enable DoH support in Chrome, users would have to use a so-called command-line argument (or command-line flag), which is a set of additional instructions that are passed to the Chrome executable at start-up, to enable in-dev features.

1. Find your Chrome shortcut. This may be on your taskbar, desktop, start menu, or somewhere else on your file system.

2. Right-click on the Chrome shortcut and select the Properties option.
![chrome-doh-rc.png](https://zdnet4.cbsistatic.com/hub/i/2019/09/08/2c48eb93-84cf-4408-8796-5aa6484d9329/1f90fe0340491c4d0a7b1c84e3c5de13/chrome-doh-rc.png)

3. In the Target field, add the following text at the end of the shortcut path and hit Save.[Source](https://bugs.chromium.org/p/chromium/issues/detail?id=799753#c8)

     ---enable-features="dns-over-https<DoHTrial" --force-fieldtrials="DoHTrial/Group1" --force-fieldtrial-params="DoHTrial.Group1:server/https%3A%2F%2F1.1.1.1%2Fdns-query/method/POST

The above text will configure Chrome to use the Cloudflare DoH server. Users can select any other DoH server from this list.

![chrome-doh-target.png](https://zdnet2.cbsistatic.com/hub/i/r/2019/09/08/a0f7384e-b8ed-44fb-a896-caf2a82ca818/resize/370xauto/85d6a9a189d6cc9efbd5abe961752d09/chrome-doh-target.png)

4.  If Chrome is already running, restart it. Otherwise, start Chrome.

5.  To test if DoH support is working in Chrome, access https://1.1.1.1/help. On the right of "Using DNS over HTTPS (DoH)" the site should return "Yes."

![chrome-doh-ok.png](https://zdnet2.cbsistatic.com/hub/i/2019/09/08/644950c8-50ec-44b6-8905-a4924c0d5a8a/ac21bfbdb1a0c2b446465191548bd5a5/chrome-doh-ok.png)


## Enabling and disabling DNS-over-HTTPS in Firefox

1. Click the menu button ![Fx57](https://user-media-prod-cdn.itsre-sumo.mozilla.net/uploads/gallery/images/2017-10-22-15-37-15-18c775.png)Menu and choose Options.

2. In the General panel, scroll down to Network Settings and click the Settings… button.

3. In the dialog box that opens, scroll down to Enable DNS over HTTPS.

   - **On**: Select the Enable DNS over HTTPS checkbox. Select a provider or set up a custom provider.

   - **Off**: Deselect the Enable DNS over HTTPS checkbox.

![image](https://user-media-prod-cdn.itsre-sumo.mozilla.net/uploads/gallery/images/2019-07-17-12-46-00-b3bf60.png)

4. Click OK to save your changes and close the window.

***Reference:***

1. *https://tools.ietf.org/html/rfc8484*

2. *https://www.zdnet.com/article/how-to-enable-dns-over-https-doh-in-google-chrome/*

3. *https://support.mozilla.org/en-US/kb/firefox-dns-over-https*



