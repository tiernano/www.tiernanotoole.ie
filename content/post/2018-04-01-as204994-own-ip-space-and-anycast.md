---
date: 2018-04-01T22:55:06Z
publishdate: 2018-04-02 00:00:00 +0100
published: true
tags:
- Networking
- IPv6
title: AS204994, Own IP Space and Anycast
slug: as204994-own-ip-space-and-anycast
aliases: 
    - "2018/04/01/as204994-own-ip-space-and-anycast.html"
---

So, if you are reading this page, it is being delivered with the magic of Anycast... Well, technically, it was before, since i used [Cloudflare](http://cloudflare.com), and it still is because of Cloudflare, but also because of my own ASN ([As204994](http://as204994.net)), some servers in different locations, and some magic, which i will explain a bit of in this post.

This all started late last year when i got my hands on an ASN and a /48 block of IPv6 addresses. I had been reading stuff about BGP, routing, etc, and decided to go all in. it was quite cheap with the help of [HostUS](https://my.hostus.us/aff.php?aff=2152). All in, it was about $50 for the year. As part of the process, i needed 2 upstream providers to say they would accept my announcement. They were [Hurricane Electric](https://www.he.net) though their [Tunnel Broker](http://www.tunnelbroker.com) service, and [Vultr ](https://www.vultr.com/?ref=6925432)using a few of their VPSs. 

After i got my space and ASN, i started to announce the V6 addresses over Vultr and Hurricane Electric, and all was good. I had 2 Vultr servers: 1 in London, UK, and one in New Jersey, USA. I had my home machine announce to HE, and then also link to both Vultr servers using [Zerotier](https://www.zerotier.com). All worked well, but due to some family issues, i never got around to putting it into production... till now.

Those 3 servers now share an IPv6 address on the loopback port. When you (well, Cloudflare) asks for that IP, the closet (network) with that IP responds, and the NGinx server on that box sends back the contents of the site. This site is hosted on each box, since its fully static, but both [AS204994 ](https://as204994.net)and [TiernanOToole.net](https://tiernanotoole.net) are hosted in Ghost, so Dublin (my machine in the house) serves them, and both Lon1 and Nyc1 do proxying. so, most requests from the US are hitting the box in NYC and the ones in Europe share either Dub1 or Lon1. I have some tweaks to do with which servers will be running where, and may add more, but currently its working well. 

So, how do you figure out what server responded? Simple. Open your Dev tools on your browser, go to network tab, refresh, and see the response headers for anything on this domain. You should see something like below.  

![](/uploads/2018/04/01/responding-server.PNG)

Over the next while, i will be updating tiernanotoole.net with more details on how this works, and more stuff will end up on AS204994.net too. If anyone notices any weird and wonderful issues, shout. If you have more questions, shout. 