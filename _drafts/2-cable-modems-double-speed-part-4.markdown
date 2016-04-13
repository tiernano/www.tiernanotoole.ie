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
title: 2 Cable Models = Double Speed? Part 4
date: 2016-04-13 21:47:00
---

[NOTE] This part 4 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double Internet/).

So, this week I went in a completly different direction that i have been thinking reciently... 


Basic thoery

* still using MPTCP kernels on both upstream and local machine
* now have 2 P2P UDP OpenVPN tunnels between house and cloud
* all TCP traffic (bar port 80) that hits the router in house is redirected to redsocks
* redsocks uses a socks server on the cloud box
* since the socks traffic is over TCP (inside the UDP OpenVPN tunnel) it uses MPTCP
* having socks running, gives me quite the download speed, turning it off does not, hence the following tweet

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Hmmmm... If I have socks on, the Internet is fast 400mb/s+). But without socks, it&#39;s down to 60... Feck...</p>&mdash; Tiernan (@tiernano) <a href="https://twitter.com/tiernano/status/720186883905626112">April 13, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

* I am also noticing that i am starting to hit the limits of my upstream VM. If downloading or uploading at speed, the processor cores (2 in the case of the box i am currently running) is pegged at pretty much 100% full... Well, 80ish, but that becuase the other 20% is being used by dante, the socks server...
* I mentioned port 80 not being set over socks. Thats because its redirected to Squid. Squid (in house) then uses Squid (in cloud) as a parent. There are 2 round-robbin parents for squid, one on each OpenVPN connection
* all other traffic (UDP, ICMP, etc) are sent over the OpenVPN connection... currently only one is picked, but I have a cunning plan... 

<iframe width="420" height="315" src="https://www.youtube.com/embed/AsXKS8Nyu8Q" frameborder="0" allowfullscreen></iframe>

So far, so good... The cunning plan? Well, if I am reading the internet correctly, and i would like to think i am, i *think* ECMP, or Equal Cost Multi-Path Routing, could help... Again, its a fledling idea currently, and i am still reading the documentation, but if it works... Well... I not sure... lets see...


