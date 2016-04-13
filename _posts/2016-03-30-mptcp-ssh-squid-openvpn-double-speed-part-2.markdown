---
layout: post
title: MPTCP, SSH, Squid, OpenVPN (and 2 Cable modems) = Double Speed? Not quite... Part 2
date: 2016-03-30 20:00:00
tags:
  - Networking
  - Projects
  - IPv6
  - Guide
  - HowTo
  - HomeLab
  - Double Internet
---
[NOTE] This part 2 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double Internet/).


In [my previous post][1] I explained what i was trying to do... This post explains what i have been working on recently, and performance results...
So, first, what have i tried... There are 3 different things i have tried, and here are some of their details. Some will need to be updated (other parts of this series), and others i will try get back to eventually.

## Hardware and servers used
To test this, i am using my [HP Proliant ML110 G5][8] running either Ubuntu or Debian Linux, with 2 GigE connections directly to the cable modems, and 1 connection to the LAN (for SSH and testing). The LAN has no gateway set, and the 2 WAN connections have DHCP enabled. They get fully public IP addresses. Upstream, I am using either [Digital Ocean][9] or [ScaleWay][10] VPS boxes.

Digital Ocean has the advantage of allowing different Kernels, so i have been using them for testing MPTCP. As for ScaleWay, well, their BareMetal C2S/M/L boxes have between 4 and 8 cores (4 for the S, 8 for the M and L) and between 8 and 32Gb RAM (S=8, M=16, L=32GB). The L model also comes with 256GB SSD (plus the boot disk, which seems to be a network disk of some sort) and they all come with lots of bandwidth (i use the L because its got about 800MBit/s to the internet).

Ping wise, Digital Ocean is about 20-30ms away from the house (I picked London to host the servers) and Scaleway is a little further at about 50ms (They are based in France).

## MPTCP ([MultiPath TCP][5])
MPTCP (their site is a bit wonky as of writing, so bare with me...) is a Linux Kernel patch that allows TCP connections to use multiple paths... Essentially, if you have Wifi and 4G in a phone, and MPTCP is enabled, it should allow you to use both connections for TCP traffic, as long as the server upstream supports it. It also allows for easy fail over if, say, you lose your wifi connection. There is an example [video of it on YouTube][6] which should show the fail over parts and [this video][7] shows how they managed to get 50Gbit/s out of a 6 10Gb Ethernet connections.

When i was using MPTCP, I had a copy of [Squid][11] on both boxes, and told Squid locally to use Squid on the upstream box (over a SSH tunnel, which was over the MPTCP link) as a parent cache. Using this method, i could see (using [iftop][12]) that both connections were being used. When trying proper performace testing, I setup a RAM disk on both machines and copied a Linux ISO to the Digtial Ocean Box. Then, using wget and [Axel][13] I downloaded the files using [Nginx][14] on the server, and checked the results. I can max out 1 single connection, plus use about 60-80mbit/s from the second. about 420-440mbit/s total. Disk was not the bottleneck, since I was writing to RAM, so more tests are required.

## MLVPN
[MLVPN][4] is a pretty interesting project that caught my eye. The idea is quite simple: you configure the local box and server, as mentioned in [their example guide][17] and run the MLVPN program on the server, then the client. It creates 2 VPN tunnels between the 2 boxes, and bonds them... In my case, i was given an IP of 10.42.42.1 on my box in house and 10.42.42.2 on the server. Any traffic over that tunnel is bonded... Problem is, it seems to be quite processor intensive: my Digital Ocean box was showing one cpu core (out of 2) maxing out at around 80% and my Proliant in house maxing around the 70% mark... all while transferring data at around 100mbit/s. I tried iperf and got the following:

![mlvpn speed test][mlvpnspeedtest]

getting 50mbit/s upload is good, in reality, since in theory my max speed would be 72, without overhead. but 116mb/s down is less than a third the max speed of a single connection. So, I tried just uploads and downloads...

Upload Only (from local machine to server)

![mlvpn upload only test][mlvpnuploadonly]

Download Only (from server to local machine)

![mlvpn download only test][mlvpndownloadonly]

As you can see, the download speed has increased a little, to 176Mbit/s, but the upload speed is now at over 60MBit/s!

Still.. download is as important as upload, and given I haven't managed to get it to max out one connection, never mind 2, even more testing is required...

## MLPPP (using VTUN)

This is one i need to come back to... Used the guide from [John Lewis][15] but was only managing to get about 100Mbit/s... I was originally using a VM (so disk may have been the issue) and also had the connection behind my EdgeRouter, so it might have been firewall rules causing a slow down. But I do need to come back to this soon... Watch this space.

## Conclusions?

Well, at the moment, all I can conclude is that there is more testing required. Upload wise, i can somewhat use most of my bandwidth with MLVPN, and I did see promising results with MPTCP. I gave up a bit too early with MLPPP, so more testing is required with that. Also, all tests are using just iperf between boxes. I did use squid with the MPTCP box for a while, but not for proper performance testing. So, even once this is all sorted out, i will need to turn this into a proper "router" too... So, conclusion? this was originally meant to be a 2 parter... now it looks like I will require a lot more parts... Watch this space...


[1]:https://www.tiernanotoole.ie/2016/03/22/2-Cable-Modems-Double-Internet-Speed-part1.html
[2]:http://bitsofnetworks.org/ovhs-overthebox-internet-access-link-aggregation-using-multipath-tcp.html
[3]:https://shadowsocks.org/en/index.html
[4]:http://zehome.github.io/MLVPN
[5]:http://www.multipath-tcp.org
[6]:https://youtu.be/VWN0ctPi5cw
[7]:https://www.youtube.com/watch?v=VMdPI9Cfi9k
[8]:https://www.tiernanotoole.ie/Computers/proliantml110.html
[9]:https://m.do.co/c/d4d345b83b55
[10]:http://www.scaleway.com
[11]:http://www.squid-cache.org
[12]:http://www.ex-parrot.com/pdw/iftop/
[13]:http://axel.alioth.debian.org/
[14]:https://www.nginx.com/
[15]:https://johnlewis.ie/bonding-teaming-internet-connections/
[16]:http://zehome.github.io/MLVPN/
[17]:http://mlvpn.readthedocs.org/en/latest/linux_example.html
[mlvpnspeedtest]:https://www.tiernanotoole.ie/post_images/2016/03/30/20160330-mlvpn-speed-test.PNG
[mlvpndownloadonly]:https://www.tiernanotoole.ie/post_images/2016/03/30/20160330-mlvpn-speed-test-download-only.PNG
[mlvpnuploadonly]:https://www.tiernanotoole.ie/post_images/2016/03/30/20160330-mlvpn-speed-test-upload-only.PNG
