---
layout: post
tags:
- RouterOS
- Windows
- Linux
- Networking
- IPv6
title: IPv6 + MikroTik + Linux + Windows
date: 2012-12-19 16:24:07
---
I have been wanting to setup an [IPv6][1] network for a while now, but never had the hardware or network to support it. My broadband Modem, a Cisco EPC3925, was pretty useless... But with the advent of [Bridging on the Cisco EPC3925][2] it now works!

The first thing i needed to do was setup a [Tunnel Broker Account][5] with [Hurricane Electric][6]. I got a /64 block of IPv6 addresses, which should do me for a while... :) 

Next, I followed the config example from the MikroTik Wiki Page: [My First IPv6 Network][4]. In my case, i only ran though most of router 1's config, and did not create the "routing between segments" and "ospv-v3" backbone... I did give my internal LAN port an IPv6 address, as well as an IPv4 address. 

Next, on my Windows Server machine, i gave it a static IPv6 address (since i dont have an IPv6 DHCP setup... yet...) and told it to use the IPv6 address i gave the RouteBoard as its gateway. Then i told it to use the [OpenDNS][7] [public IPv6][8] address. I then visited [IPv6 Test][9] and [Google's IPv6 page][10] to confirm connectivity... SUCCESS!!!

On my Linux box, I followed [Soflayer's Adding an IPv6 IP][11] tutorial. 

So far, so good... 

[1]:http://en.wikipedia.org/wiki/Ipv6
[2]:http://tiernanotoole.ie/2012/10/02/Enabling-true-briding-mode-on-Cisco-EPC3925.html
[3]:http://knowledgelayer.softlayer.com/questions/468/Adding+IPv6+to+Ubuntu+systems
[4]:http://wiki.mikrotik.com/wiki/Manual:My_First_IPv6_Network
[5]:http://www.tunnelbroker.net/
[6]:http://www.he.net
[7]:http://www.opendns.com
[8]:http://www.opendns.com/ipv6
[9]:http://www.ipv6-test.com
[10]:http://ipv6.google.com
[11]:http://knowledgelayer.softlayer.com/questions/468/Adding+IPv6+to+Ubuntu+systems