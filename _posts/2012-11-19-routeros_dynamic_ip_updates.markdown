---
layout: post
tags:
- Hardware
- Networking
- RouterOS
title: RouterOS Dynamic IP Updates
date: 2012-11-19 10:19:26
---
I have been using a [MikroTik][1] [RouterBoard RB750][2] for a while now, and i love it! Over the weekend, i upgraded it to a [RB1100][3]. Its the same software running the device, but the device is faster (800Mhz PowerPC chip VS MIPS-BE at 680Mhz), has more memory (512Mb upgradable to 1.5Gb vs 32Mb) and more storage (think its 512Mb on board, plus 4Gb MicroSD card vs 32mb...). It also has more ports (13 GigE VS 5) and 2 Switch Groups, which i have no idea what they do just yet...

Anyway, part of getting the RB1100 online and taking over from my existing router was getting Dynamic DNS updating. I use both [Dyndns][4] and [NoIP][5] for DNS, but I also like the look of [Amazon Route 53][6]. For updating NoIP, I am using the Alternitive script from [The Mikrotik Wiki][7]. To get this to work with DynDNS, it would just be a matter of chaning the URL you point to... I am going to write a web script which will sit internally on the network, use that instead of the No-IP url. When that script gets called, i can log the info, update DynDNS, NoIP and Router53 all in one go. I will be posting more about that soon...

And while we are on the topic of Scripting RouterOS, checkout the [Mikrotik Script Example Page][8]. Lots of good stuff up there!

[1]:http://www.mikrotik.com
[2]:http://routerboard.com/RB750G
[3]:http://routerboard.com/RB1100
[4]:http://www.dyndns.org
[5]:http://no-ip.com
[6]:http://aws.amazon.com/route53
[7]:http://wiki.mikrotik.com/wiki/Dynamic_DNS_Update_Script_for_No-IP_DNS
[8]:http://wiki.mikrotik.com/wiki/Scripts
