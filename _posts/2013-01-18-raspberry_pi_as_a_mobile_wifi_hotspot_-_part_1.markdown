---
layout: post
tags:
  - Raspberry Pi
  - Networking
  - Projects
title: Raspberry Pi as a Mobile WiFi HotSpot (part 1)
date: 2013-01-18T07:57:16.000Z
---

I have been using an iPhone 4 as a wifi hotspot for a while now. It does not have a "phone" SIM in it, with calls and texts enabled, instead it has a 3G Data SIM from a dongle... It works OK, but there are a few issues i have with it...

* No easy way to see how much data is being used, unless you Jail Break, and then battery life goes away...
* not very hackable... other than Jail Break, and thats not hackable enough...
* not a lot of storage: 16Gb, and most of that is takin up by Music and Apps
* no background network daemons... more on that in a second...

The Network Daemons i am thinking would be useful for a WiFi Hotspot would be [Squid][1], [WANProxy][2], SSH, PPTP or OpenVPN Client and possibly a downloader of some sort. What i am thinking is as follows:

* Have a device, that is small enough to fit in a bag, possibly small enough to fit in a jacket pocket. It will probably not be as small as the iPhone.
* It should have storage on board. Boot storage and cache storage
* At least 1, possibly more, WiFi Adapters, with optional antennas
* At least 1, possibly more, 3G or 4G Modems
* At least 1 ethernet port, again possibility for more
* Battery that can run the whole system for at least 4-5 hours, and should be able to run while being charged. charging via USB would be ideal also
* Optional Screen, but more likley, some sort of web interface to show whats going on (Bandwdith usage, clients connected, connection details)

When this turns on, it should automatically start the 3/4G connections (if there are multiple connections, it should do some balancing of the connections). if there are more then 1 WiFi Connection, one should be a Client (connect to an external WiFi connection, like home, college, work) and one should be an Access Point (Your Phone, Tablet and Laptop connect to this one). Ethernet can also be used in a simular way (if one only, it could be client or server, if multiple, one can be client, one can be server). DHCP addresses will be given out on Access Point or Server connections, and on Client connections, DHCP will be accepted.

Squid would be installed and listen on its usual port. Optionally, all port 80 and 8080 traffic could be routed though Squid. Ideally, HTTPS traffic should be automatically routed, but i think thats a bit harder to setup... If VPN Clients are enabled, it could also allow All or Some traffic to be routed over the VPN connections. SSH could also be used to compress traffic between multiple Squid boxes (one in house, one on the device). WANProxy could be used in a simular manner to save bandwdith and make the connection faster.

So, with all that, i am looking at using a [Raspberry Pi][3] for the job. I am still working on this, but here is what i have so far...

* I have put a Wifi adapter into my Raspberry Pi (A Linksys, but forget the exact model number). Using a tutorial on [Vivek's blog on making a wifi hotspot on linux][4] i managed to get the AP showing up on my laptop, but could not connect. I am not sure if its the adapter causing the problem, or what, but i am going to change out the adapter.
* At the moment, i am sharing the ethernet connection, not the 3G connection... I have posted here before the [link to Terence Eden's post on getting the Raspberry Pi to connect to 3G][5]. All that i will need to do is connect to 3g and then NAT the connection from Wifi to 3G...

So, there are a few more bits and pieces to get done over the next while... I will keep posting here...

[1]: http://www.squid-cache.org
[2]: http://wanproxy.org/
[3]: http://www.raspberrypi.org/
[4]: http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/
[5]: http://shkspr.mobi/blog/2012/07/3g-internet-on-raspberry-pi-success/
