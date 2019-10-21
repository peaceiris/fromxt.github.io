---
title: "Install Mercury's MW150UH/300UH WiFi USB Adapter driver on Unbunt 18.04"
date: 2018-09-14T13:41:59+08:00
categories:
  - "computer"
tags:
  - "computer"
  - "ubuntu"
  - "driver"
---

The MW150UH/MW300UH 11N Wireless USB Adapters auto-sensing capability allows high packet transfer rateof up to 150Mbps/300Mbps for maximum throughput. It has good capability on anti-jamming; it can alsointeroperate with other wireless products. The adapter supports WEP, WPA and WPA2 encryptionto prevent outside intrusion and protect your personal information from being exposed. But we can only download the Window verison drives for them from official  website. But How to make enable the wifi adapters on Ubuntu 18.04.You can follow the steps below.
<!--more-->

## Mercury  MW150UH

![MW150UH](https://imgurl.org/temp/1809/aee67c46d3a739ab.jpg)

Mercury MW150U Wifi USB adapter includes embedded the chip of Realtek RTL8188CE, you can install it instead.

1. Download Realtek [RTL8188CE linux driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

2. Save the Downloaded zip file and extract the Driver package.

3. Type “make all && sudo make install" the driver package will start compiling.



## Mercury  MW300UH

![MW300UH](https://imgurl.org/temp/1809/c30ebd5748b34312.jpg)

Mercury MW300UH Wifi USB adapter includes embedded the chip of REALTEK RTL-8192EU, So we can install rtl8192eu-linux-driver on Ubuntu 18.04.
The Linux Driver at [Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver) is one of the only working driver packages for the Realtek 8192eu chipset WiFi Adapters.

1. Just go to the main page [here](https://github.com/Mange/rtl8192eu-linux-driver) and click on the Green “clone or download” button.

2. Save the Downloaded zip and Extract the package, *cd* to the directory.

3. Sudo make && Sudo make install in the terminal and press “Enter” and the driver package will start compiling.

4. **If you have upgraded to Linux kernel >= 4.9.x and the RTL8192EU has stopped working.** do the following:

  - Open **+“/etc/modules”** from Root File Manager by a text-editor (Leafpad, Gedit. etc..)
  - Add an entry **“8192eu”** without the quotation marks to the “etc/modules” above.
  - Recompile the driver using “sudo make && sudo make install” as in Step-3 above:

5. Reboot and the RTL8192EU will start working.

