---
title: "Chrome 69 no longer displaying www in domain names"
date: 2018-09-07T13:23:28+08:00
categories:
  - "Miscellaneous"
tags:
  - "chrome"
  - "google"
---

As we know, Chrome 69(9.0.3497.81)has reached the stable branch and is now available for us on September 4, 2018, When you update to the lastest version, you will find that Chrome 69: “www.” subdomain is missing from URL,.

Google suddenly cuts characters from address bar for the sake of brevity (yeah right), confusing the heck out of us.The truncation is the result of Chrome programmers considering www to be a "trivial" subdomain, and setting it to be removed from the address bar.
<!--more-->
But I think that it is a dumb change. No part of a domain should be considered “trivial”. We often have to go to great lengths to teach users that “www.domain.com” and “domain.com” are two different domains, and that they may not necessarily go to the same destination. The marketing world has done a lot of damage convincing people that “www” is both ubiquitous and non-essential, when in fact, for some domains, the use or lack of it can be quite important to getting to the correct location. 

Users who want to reenable the full display of subdomains can do so by changing a flag setting at <font color=#0000FF >chrome://flags/#omnibox-ui-hide-steady-state-url-scheme-and-subdomains</font>.Clicking in the URL bar to edit the address also shows the full string. 


Reference:

- [https://www.reddit.com/r/programming/comments/9dlt83/chrome_no_longer_displaying_www_in_domain_names/](https://www.reddit.com/r/programming/comments/9dlt83/chrome_no_longer_displaying_www_in_domain_names/)

- [https://bugs.chromium.org/p/chromium/issues/detail?id=732582](https://bugs.chromium.org/p/chromium/issues/detail?id=732582) 

- [	https://news.ycombinator.com/item?id=17927972](https://news.ycombinator.com/item?id=17927972)





