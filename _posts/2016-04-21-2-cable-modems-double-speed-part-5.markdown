---
layout: post
title: "(Mad) Max Speed - The Road Warrior (Internet connection) (double speed internet Part 5)"
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
date: "2016-04-21 21:33"
published: true
---

[NOTE] This part 5 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double Internet/).

This post is going to be an update and theoretical post. probably very little "new" stuff going on here, mostly updates, and what I am planning on doing later on.

This week, I have been [OOF][1] sick, so I have not done much work, but I have been surfing the web, watching videos, downloading stuff, etc., so I have an idea of how things are going. First, as mentioned in [the previous post][2] I have MPTCP, Squid, Socks Servers, OpenVPN and IPTables doing their magic. 2 [OpenVPN][5] tunnels between the house and [Digital Ocean][3]. All TCP Traffic (bar port 80) is sent over socks to the box in the cloud using RedSocks. All UDP traffic is sent direct over OpenVPN. Since MPTCP is in the mix, all socks traffic is actually split over the 2 connections. All port 80 traffic, and 443 (if the client is using local Squid as their proxy) is sent round-robin between the 2 upstream IPs to Squid (2 OpenVPN end points).  

Things I have noticed:

* Every now and again, [RedSocks][4] crashes... just full on dies. It’s just a matter of starting again, but it’s a pain...
* I have had to restart squid a couple of times... not too often though
* there was a power outage in the house a few days back... so, when everything came back online, it was a bit of a pain bringing all connections back to life. I do have to figure out a better plan

I still have to read more on this ECMP stuff. Hopefully it will do what I am hoping.

Now for the theoretical stuff. I started thinking, could this work outside the house? Could you build this into something smaller, like a Raspberry Pi, and stick 2 or more USB Modems in, connect it back to a server in the cloud, setup P2P OpenVPN connections and then get more than a single modem speed download? The problems I can see are around MPTCP. I am not sure if it has been ported to ARM to run on a Raspberry Pi. Second, the max you could ever get out of it is 100Mbit/s, given the 10/100mb network port on board... and you may need extra power for the USB dongles. Also, getting P2P connections may be complicated, given the non-static IPs on the modems, though, in theory, non-P2P OpenVPN could work... Again, it’s a theory. I had the though and that’s where the title came from... anyway, throwing it out there...


[1]:http://blogs.technet.com/b/exchange/archive/2004/07/12/180899.aspx
[2]:https://www.tiernanotoole.ie/2016/04/14/2-cable-modems-double-speed-part-4.html
[3]:https://m.do.co/c/d4d345b83b55
[4]:https://github.com/darkk/redsocks
[5]:http://www.openvpn.net
