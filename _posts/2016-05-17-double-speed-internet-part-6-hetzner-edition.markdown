---
layout: post
title: "double speed Internet Part 6 - Hetzner Edition"
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
date: "2016-05-17 13:00"
published: true
---

[NOTE] This part 6 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double%20Internet/).

Its been a while, since I posted, and there are some, well, pretty major changes since the last time... Lets start are the beginning.

Last time I was using [Digital Ocean][1] for my hosting provider. I was using their $20 a month server (2 cores, 2GB RAM, 40GB SSD, 3TB transfer), and it was all good... But I noticed that every now and again I would need to reboot the box. I also noticed that when transferring large files or using higher bandwidth (400mb/s+) the 100% of both cores were being used. So, I wanted to move to something with more power...

I also was limited to IP addresses. Yes, Digital Ocean do offer IPv6, but I could only get 1 IPv4 address... and I wanted more...

So, I went back to some old friends of mine, [Hetzner][2], and bought a dedicated server with a Quad Core Xeon E3, 32GB RAM, 4*3 TB HDDs, 1Gbit/s network connection with 30TB transfer per month and a KVMoIP plugged in. I also got 2 extra standard IPs and a /29 (8 IPs, 6 usable). I will explain that next. I installed Debian 8.4 on the first disk, and I am planning on using the other 3 for storage of some sort. I then installed the [MPTCP kernel][3], [OpenVPN][4], Squid and a Socks server (same as the Digital Ocean box) and reconfigured the home machine... All good! Now when browsing the web, everywhere thinks I am in Germany, but so far, so good... Speed tests are about the same, but I have my theory about [ECMP][5] to try this weekend.

Because of the extra IPs, I am working on doing full IP forwarding, not just port forwarding. One of my IPs in pointing directly at my [Meraki MX64][6] in house (a post on the Meraki stuff is coming, eventually...) and another at the [Proliant box][7], and I plan on pointing other IPs at machines in the DMZ or a firewall of some sort. the /29 is routed though the IP pointing at the Proliant, so that makes life easier. The original IP is only used for SSH and OVPN from the house. it should not do much else. All network traffic in house is coming from other of the other IPs. 

Again, so far, so good. Hopefully the ECMP stuff works correctly, so I will do an updated post soon. 

[1]:https://m.do.co/c/d4d345b83b55
[2]:http://www.hetzner.de/en
[3]:http://www.multipath-tcp.org
[4]:http://www.openvpn.net
[5]:https://en.wikipedia.org/wiki/Equal-cost_multi-path_routing
[6]:https://meraki.cisco.com/products/appliances/mx64
[7]:https://www.tiernanotoole.ie/Computers/proliantml110.html
