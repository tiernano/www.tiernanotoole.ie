---
layout: post
tags:
- Networking
- Ubiquiti
- Hardware
- HomeLab
title: Ubiquiti EdgeRouter PoE in the lab
date: 2015-08-05 21:00:00
---
Today, my [Ubiquiti EdgeRouter POE][1] arrived in the house. I got it hooked up to both UPC connections (as secondary connections) and all seems to be working grand. Some notes i wanted to put up here:

* out of the box, the install was quite simple. set my Ethernet connection to a static ip in the 192.168.1.x/24 range,
using 192.168.1.1 as gateway and dns, and then point at http://192.168.1.1 for admin. login (ubit for both username and
password) and heay presto. I was asked did i agree to the license, and then im in.
* by default, NAT is off... i turned it on, and enabled DNS and was able to surf.
* I also noticed the software was out of date... Oddly, there did not seem to be an option to update automatically, but
you can manually download the tar and upload it, which i did.
* so far, so good... not sure yet if i will be using it as my main router, but it may end up being a VoIP router.

Finally, speed test result below:

![Speed Test Result](https://www.tiernanotoole.ie/post_images/2015/08/05/20150805.ubiquiti.speedtest.compressed-resized.jpg)

More [Ubiquiti][2] stuff arriving tomorrow... will post more stuff then.

[1]:https://www.ubnt.com/edgemax/edgerouter-poe/
[2]:https://www.ubnt.com
