---
layout: post
tags:
- Raspberry Pi
- Hardware
title: Raspberry Pi now with 512MB RAM, other random links...
date: 2012-10-15 12:37:20
---
Earlier on today, the Raspberry Pi Foundation announced that the Model B will now be [shipping with 512Mb RAM as standard][1], with no price change. I posted the link up on [Hacker News][2] and its caused quite a lot of happy people! 

So, with the news of extra RAM, its started making me think of more things the Pi could be used for...

* An Austrian hosting company [are offering free Co-Location for Raspberry Pis][3] with a 100Mb/s uplink and 100Gb bandwidth! FREE! with 512Mb RAM (or even 256Mb RAM) thats enough for a small site. or even a medium site (like this one) running statically. 
* Since the [Pi can connect to the internet using 3G][4], you could install a copy of [Squid][5] and use an SSH tunnel back to your main office or home, have have multiple levels of caching going on... It would also secure your browsing. 
* [Sending SMS messages though the Raspberry Pi][6] could be useful for sending diagnostic info if the device is remote... 
* [XBMC on the Raspberry Pi] would make your media center a lot smaller, use less power, etc. 

just a note on the idea of using 3G and Squid for the Pi... This is something i am interested in, so its something i want to start playing with. The idea would be as follows:

* have a linux box in house with Squid and SSH enabled, and port forward SSH to the linux box. 
* tell the pi, on boot, to try and connect to a 3G connection.
* once connection is live, connect to SSH tunnel
* Squid should already be configued to load and use the upstream Squid box as an upstream cache
* local squid should use some storage on either USB or SD for local cache

Also, using something like [WANProxy][8] on both ends should make things faster also... Having the Pi, a 3G modem, USB key (optional) and a battery pack, all in a small box, with a Wifi Adapter, should give you a faster mobile internet connection... And if you could get 2 or more 3G modems (using a Powered USB Hub of some sort), you could do load balancing... 

[1]:http://www.raspberrypi.org/archives/2180
[2]:http://news.ycombinator.com/item?id=4654251
[3]:https://www.edis.at/en/server/colocation/austria/raspberrypi/
[4]:http://shkspr.mobi/blog/2012/07/3g-internet-on-raspberry-pi-success/
[5]:http://www.squid-cache.org/
[6]:http://shkspr.mobi/blog/2012/06/raspberry-pi-python-and-3g-dongles-oh-my/
[7]:http://wiki.xbmc.org/index.php?title=Raspberry_Pi
[8]:http://wanproxy.org/