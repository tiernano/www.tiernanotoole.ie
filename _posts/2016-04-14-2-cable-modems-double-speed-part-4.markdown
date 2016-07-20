---
layout: post
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
title: "2 Cable Modems = Double Speed? Part 4"
date: "2016-04-14 08:55"
published: true
---

[NOTE] This part 4 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double%Internet/).

So, this week I went in a completely different direction that I have been thinking recently...


So, the basic theory is as follows:

* I am still using MPTCP kernels on both upstream and local machine
* now have 2 P2P UDP [OpenVPN][2] tunnels between house and cloud. Example config is [here][1]
* all TCP traffic (bar port 80) that hits the router in house is redirected to [RedSocks][3]
* RedSocks uses a socks server, [Dante][4], as an upstream server on the cloud box
* since the socks traffic is over TCP (inside the UDP OpenVPN tunnel) it uses MPTCP
* having socks running, gives me quite the download speed, turning it off does not, hence the following tweet

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Hmmmm... If I have socks on, the Internet is fast 400mb/s+). But without socks, it&#39;s down to 60... Feck...</p>&mdash; Tiernan (@tiernano) <a href="https://twitter.com/tiernano/status/720186883905626112">April 13, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

* I am also noticing that I am starting to hit the limits of my upstream VM. If downloading or uploading at speed, the processor cores (2 in the case of the box I am currently running) are pegged at pretty much 100% full... Well, 80ish, but that because the other 20% is being used by Dante. I am noticing I can hit a full 72Mbit/s up, but the max currently downloading is about 400, maybe 450... Need a faster box now...
* I mentioned port 80 not being set over socks. That's because its redirected to Squid. Squid (in house) then uses Squid (in cloud) as a parent. There are 2 round-robin parents for squid, one on each OpenVPN connection IP address.
* all other traffic (UDP, ICMP, etc.) are sent over the OpenVPN connection... currently only one is picked, but I have a cunning plan...

{% youtube AsXKS8Nyu8Q %}

The cunning plan? Well, if I am reading the internet correctly, and I would like to think I am, I *think* [ECMP][5], or Equal Cost Multi-Path Routing, could help... Again, it’s a fledgling idea currently, and I am still reading the documentation, but if it works... Well... I not sure... let’s see...


[1]:https://gist.github.com/tiernano/09c6928d1d8f6752ea84fd895451bbe5
[2]:http://www.openvpn.net
[3]:https://github.com/darkk/redsocks
[4]:http://www.inet.no/dante/
[5]:https://en.wikipedia.org/wiki/Equal-cost_multi-path_routing
