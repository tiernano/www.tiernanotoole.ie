---
layout: post
title: 2 Cable modems = Double Internet Speed? Well... not really... Part 1
date: 2016-03-22 18:00:00
tags:
- Networking
- Projects
- IPv6
- Double Internet
---
[NOTE] This part 1 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double Internet/).

First, a bit of background, and then I will explain what I am currently running in [Part 2][14]...

For the last 15 or so years, I have had at least 2 internet connections in to the house... 2 of them have always been Cable Modems from NTL, which became UPC, and now is [Virgin Media][1]. When I started, i think the modems where 150/50kbit/s and 600/150kb/s, and have steadily increased in speed, currently at 360/36Mbit/s each... But they have always been somewhat separate, and single thread downloads have always been limited to 1 of the connections... I have been looking for ways around this for years...

It started with a [Linksys RV042 router][2] which allowed me to load balance my connections... At the time, and i cant even remember when this was, my total bandwidth would not exceed the router. The RV042 has 2 10/100mbit WAN links and 4 100mb/s LAN links...So, when the connection bandwidth increased, I moved to a new router...

The next router vendor i tried was [Mikrotik][3]. I tried a few different options, including an [RB1100][10] and running their [RouterOS][11] on x86 hardware... Both worked, well, ok, and the [Load balancing with nth][9] stuff did do what i needed, along with other stuff, like routing traffic destined for some sites (like BBC iPlayer) to go over a VPN. But in the end, hardware issues and performance problems with the x86 machine (Mikrotik at the time was limited to 2GB of RAM on x86 hardware) I ended up at [PfSense][4].

PfSense was installed on the same hardware, a HP ProLiant ML110 G5 with 8GB RAM, a Core2Quad processor and 12 GigE Network cards... And, on PfSense, things were good... Performance was stable, load balancing worked as expected, I could set some traffic to go over certain links, etc. all was good... But I lacked IPv6... Plus, the HP used a LOT of power...

The current instalment of my network uses a [Ubiquiti Networks][5] [Edge Router POE][12]. To show the difference in power, check out the graphs from my [Ubnt MPower][13] device. ProLiant first, EdgeRouter second:

![Proliant Power Usage](https://www.tiernanotoole.ie/post_images/2015/09/16/20150916-proliant-power-usage.PNG)

![EdgeRouter POE Power Usage](https://www.tiernanotoole.ie/post_images/2015/09/16/20150916-edgerouter-power-usage.PNG)

Plus, the EdgeRouter does not produce as much heat, and its a LOT smaller that the PowerEdge! It does all the same things I could get PfSense to do, in a lot smaller package (I could, in theory, get a smaller box for PfSense).

So, where does that leave us? Well, I now have 720Mbit/s down and 72Mbit/s up, if I can do multiple threads for uploading... But what if I don't? What's next? Well, in the second post, I will explain what I have been trying to do in resent weeks, and what I can do now...

[1]:http://www.virginmedia.ie
[2]:http://www.cisco.com/c/en/us/products/routers/rv042-dual-wan-vpn-router/index.html
[3]:http://www.mikrotik.com
[4]:http://www.pfsense.org
[5]:http://www.ubnt.com
[6]:http://www.multipath-tcp.org
[7]:http://www.squid-cache.org/
[8]:http://www.openvpn.net
[9]:http://wiki.mikrotik.com/wiki/Load_Balancing#Nth
[10]:http://routerboard.com/RB1100
[11]:http://www.mikrotik.com/software
[12]:https://www.ubnt.com/edgemax/edgerouter-poe/
[13]:https://www.ubnt.com/mfi/mpower/
[14]:https://www.tiernanotoole.ie/2016/03/30/mptcp-ssh-squid-openvpn-double-speed-part-2.html
