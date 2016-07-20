---
layout: post
title: "double speed Internet Part 7 - ECMP (kind of)"
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
date: "2016-05-31 06:00"
published: true
---

[NOTE] This part 7 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double%20Internet/).

In the [last post][1] I mentioned I am now using [Hetzner][2] for hosting a dedicated box. Thats still live, and going well. I have a /29 IP range (6 usable) and also 2 other IPs. So far, so good... But because i was using a Socks Server, I was not fully able to use the /29 ips... I use something like as follows:

<script src="https://gist.github.com/tiernano/68894593dd44acb4820617aef2889fd6.js"></script>

essentially, for each public IP i have that i want to map to an internal IP, i have a POST and PRE ROUTING rule, plus the required forward rules... But, if socks are used, then that goes out the Window, since TCP traffic will look like its coming from the socks server... So, i killed the socks server, removed the IPTables rule, and then realized that while outgoing traffic was being balanced somewhat (2 default rules on the internal box pointing at the OpenVPN IPs from the Hetzner box) incoming was a problem. Hetzner knew how to get to my internal network, but only though one ip... enter Quagga and Zebra...

[Quagga][3] is a routing software suite, which can do protocols like OSPF, BGP and RIP, and Zebra is the component that does static routing. using their [documentation on static routes][4], I created a static route to my internal network with 2 next hops, the OVPN IPs from the internal box... and, after restarting Quagga, all works! happy days! now i can forward ips from outside the network to inside the network correctly, and they look like they are the public ip! 

So, whats next then? well, I now have a server in Germany (Hetzner) and one in France ([OVH][5]), and can spin one up in the UK or the US ([Digital Ocean][6]). Given that i have Quagga running on the box, i am now thinking of trying to see if its possible to route traffic depending on distance or something similar... If i am trying to hit a server in Hetzner's DC, i should go though Germany. If its in Digital Ocean, go though either US or UK servers, same with OVH. Then figure out who has the fastest links to, say, Amazon, Azure, Netflix, BBC, Dropbox, etc, and add either static or dynamic links to the router... essentially, thats the theory... lets see how that works...


[1]:https://www.tiernanotoole.ie/2016/05/17/double-speed-internet-part-6-hetzner-edition.html
[3]:http://www.nongnu.org/quagga/
[2]:http://www.hetzner.de/en
[4]:http://www.nongnu.org/quagga/docs/docs-info.html#Static-Route-Commands
[5]:http://www.ovh.com
[6]:https://m.do.co/c/d4d345b83b55
