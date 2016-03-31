---
layout: post
tags:
  - Networking
  - PFSense
  - Hardware
  - HomeLab
title: Network and HomeLab V.Next (Part 2)
date: 2015-06-23T10:30:00.000Z
---

So, in my last post i talked about the requirements for the home lab, and in this post, im going to talk about a few more updates i have made in the last few weeks.

First, the processors: in the first post, i talked about Xeon D or Xeon E3... Well, i missed one... The Xeon E5. I have 2 of these in GodBox 2, and you can get them into a [microATX board](http://www.servethehome.com/asrock-rack-epc612d4i-review-mitx-xeon-e5-platform/). There does seem to be some limits with the microatx boards, but hopefully enough searching will find me what i am looking for. Ideally, i want it to take "normal" DDR3/4 memory (not SODIMMs like the ASRock one above) and also take enough of them to run 64 or 128Gb of ram (thinking 8 would do the job!). Also, i would like to have 4 GigE ports onboard and 1 management port. 4 onboard is not a hard requirement: If i can get one with 2 ports, i can always get a 4 port card for the PCI-Express slot... Finally, i would like it to have at least 6 SATA ports and possibly an MSATA port. Thinking Boot off MSATA ([Windows Server 2016 Nano Server](https://en.m.wikipedia.org/wiki/Windows_Server_2016) would be used), 2 SSDs and 4 HDDs. Using Storage Spaces, use the 2 SSDs as "Fast" storage for the pool.

I also think i moved off the idea of 10Gb. I like the idea of it, but given a small 10Gb switch costs upwards of a grand, and the plan is to build a machine for that price, i would prefer a fifth machine and using my existing Cisco 48 port switch and leave 10Gb as a future upgrade.

Also, changed from last time round is machine count. Originally i was saying 3-4 machines... now i am thinking 6-7... 5-6 of them should be Hyper-V boxes and the last one would be a Media Box.

I also think the Synology or SAN requirement is out... Hyper-V can be setup to do replication between hosts, and with a 4Gb link to the LAN, i think i should be OK. Also, if i have the media box separate, i should be ok there too. I will detail the media center in a later post.

So, any suggestions or thoughts on what should and shouldn't be looked at?
