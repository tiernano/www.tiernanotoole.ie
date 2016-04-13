---
layout: post
title: 2 Cable modems = Double speed? Part 3
date: '2016-04-02 17:48'
tags:
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
---
[NOTE] This part 3 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double Internet/).

In [Part 1 of this series][1] I explained the why and what I wanted to do for this "project". In [Part 2][2] I did some basic testing of both [MPTCP][3] and [MLVPN][4]. I also mentioned trying [MMPPP][5] using [vtund][6] but it has been a while since I did that testing, and it had not been on bare metal. So, this post is a follow up, where I am using bare metal.

So, first, the setup:

* ProLiant box is running Debian 8.3 x64, and has both vtund and ppp installed
* [Digtial Ocean][7] box also has Debian 8.3, vtund and ppp installed
* walked though the guide from [John Lewis][8] and made some changes to the configs. the main ones are mentioned below

Once done, i installed both iperf and iftop on both boxes, and ran

    iperf -s

on the Digital Ocean box and

    iperf -c 192.168.10.1 -d

on the local box. And, well, the results where not as expected. Pretty poor actually:

First, using Squid installed on the DO box, i tried using WGET to download a file using it. If I did this on the DO box itself, i was getting 100MBytes/s... When I ran it over the MLPPP box, well, under 7 was achieved.

[![WGET over Squid over MLPPP](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-downloading-over-mlppp.PNG)](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-downloading-over-mlppp-orig.PNG)

Then i though it might have been Squid. So, since the file had been downloaded to DO, i SFTPed into the box over the MLPPP link, and tried again... Again, pretty poor result. I think i seen it hit about 7MB a sec at one stage.

[![SFTP over MLPPP](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-sftp2-over-mlppp.PNG)](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-sftp2-over-mlppp-orig.PNG)

Here is what is showing on the DO box when running the SFTP download. You can see 2 connections from the 2 WAN links at home hitting the box, and they are balanced. Its just nowhere near the speed they are capable of.

[![iftop running on server](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-sftp-over-mlppp.PNG)](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-sftp-over-mlppp-orig.PNG)

I did not get a screen shot of this, but when I tried with iperf, thinking it might have been overhead of SFTP or Squid, I was getting results matching what I was seeing with SFTP. Downloads in the 55-60mbit/s range for download and 40ish for upload. 40 is still faster than 1 link, mind you...

I mentioned that I had made some minor tweaks to the configs from what John had written. Well, mostly it was config changes to how routing was done. In Johns case, he is bonding a DSL and a HSDPA connection, so he had setup to do for logging into his PPP modem and connecting. Also, when he setup the interfaces, he routing tables in there. I have mine setup in a single config file, like as follows:

<script src="https://gist.github.com/tiernano/a9a642c4d029c0dcf8beb926b3588991.js"></script>

I have changed the names from adsl1 and 2 to WAN1 and 2, and the IPs are changed from internal IPs to my public IPs. I manually run this when setting up my connection.

Nothing else on his config files have changed. I did not do any of the masquerading stuff, mainly cause this was testing. I just want a tunnel to start with. When reading the vtund.conf file, you can see that encryption and compression are both turned off, and and the same in the ppp configuration. I also don't think the issue is to do with the CPU performance, since these are the screenshots of top running on both boxes:

[![Top on Server](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-top-view-server.PNG)](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-top-view-server-orig.PNG)

[![Top on Client](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-top-view-client.PNG)](https://www.tiernanotoole.ie/post_images/2016/04/02/20160402-top-view-client-orig.PNG)

in both cases, CPU usage is sub 6% for VTUN and SSH seems to be using less than 10%. So, now, I'm baffled as to why this is not performing as expected... More testing required!

[update 4/4/2016] - fixing images so they are clickable...


[1]:https://www.tiernanotoole.ie/2016/03/22/2-Cable-Modems-Double-Internet-Speed-part1.html
[2]:https://www.tiernanotoole.ie/2016/03/30/mptcp-ssh-squid-openvpn-double-speed-part-2.html
[3]:http://www.multipath-tcp.org
[4]: http://zehome.github.io/MLVPN
[5]: https://en.wikipedia.org/wiki/Point-to-Point_Protocol#PPP_Configuration_Options
[6]: http://vtun.sourceforge.net/
[7]:https://m.do.co/c/d4d345b83b55
[8]:https://johnlewis.ie/bonding-teaming-internet-connections/
