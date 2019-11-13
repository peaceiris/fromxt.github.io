---
title: "How to solve slow boot on Ubuntu"
date: 2019-11-13

categories:
  - "computer"
tags:
  - "ubuntu"
---

I just installed Ubuntu on my old laptop, and everything seems to work well, except booting the system. It could take several minutes to an hour or more  to login desktop. After logging in, there's a black screen and my cursor, nothing else! I found out that `drm_kms_helper-errors` occur repeatedly and takes a lot of time each. What does this mean and how do I fix it? If it can't be fixed, how do I prevent it from using so much time when booting?
<!--more-->

To avoid delay you can use workaround. From terminal run:

1. `sudo gredit /etc/default/grub`
Then add the kernel boot parameter: **`video=SVIDEO-1:d`**, so it will look like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=SVIDEO-1:d"

2. `sudo update-grub`

3. `sudo reboot`


Meanwhile,I found this entry (https://bugs.archlinux.org/task/51703) with this issue:

>Comment by Luis Bourgard (unnilquadium) - Friday, 26 January 2018, 19:08 GMT Still present in 4.14.14 It only happens with the xf86-video-intel package installed (running on a laptop with intel integrated graphics on an i5-2410m). Uninstalling that package fixes the issue, but it also introduces some screen tearing.
