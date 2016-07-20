---
layout: post
title: "double speed Internet Part 8 - Routing Around"
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
date: "2016-06-08 08:00"
published: true
---

[NOTE] This part 8 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double%20Internet/).

At the end of my [last post][1] I asked the question about routing traffic to different servers based on thier distances, etc... Well, after a bit of messing, i can say it kind of works! here is a quick over view:

* server in the house has now got multiple OpenVPN connections (2 to [Hetzner][5], 1 to [OVH][6] (with a plan to double), 1 to [Digital Ocean][7] (again, to be doubled) and i am planning 2 to [Azure][8] as well).
* [Quagga/Zebra][12] has static routes (currently static, planing on dynamic soon... more eventually) to different servers depending on where they are. for example, all traffic to the hetzner network (including their [Storage Boxes][2]) go though the hetzner link. [Hubic][9] traffic goes though OVH, Azure (currently) and AWS traffic, aswell as some CDNs go direct over either WAN1 or WAN2 in the house, and some other stuff ([CrashPlan][10] currently) goes though Digital Ocean. Everything that has no static route goes though Hetzner...
* Ideally, the static side of things should be removed, and a more dynamic setup done. How that works, i have no idea... [Spotify][11] have 2 posts about their SDN Internet Router ([part 1][3] and [part 2][4]) which is an interesting idea... More digging and research is required.

So, there you have it. Everything currently seems to be working, mostly, and tweaks can be made easily... I have a couple posts i have in my head, including something to do with automating bringing up new machines (probably with [Ansible][13] or something like it), more monitoring, and some other stuff too... Any questions, leave a comment, and i will get back.

[UPDATE] I wrote a quick and dirty app called [WhoIsToZebraConfig][14] which takes an AS Number, looks up the info in the [Merit RADb][16] (with the help of some code from [Coder Buddy][15]) and outputs what you need to put into your Zebra Config... should save me some time, and it might save you time too...  shout if you have questions!

[1]:https://www.tiernanotoole.ie/2016/05/31/double-speed-internet-part-7-ecmp-kind-of.html
[2]:https://www.hetzner.de/en/hosting/produktmatrix/storagebox-produktmatrix
[3]:https://labs.spotify.com/2016/01/26/sdn-internet-router-part-1/
[4]:https://labs.spotify.com/2016/01/27/sdn-internet-router-part-2/
[5]:http://www.hetzner.de/en
[6]:http://www.ovh.ie
[7]:https://m.do.co/c/d4d345b83b55
[8]:http://www.azure.com
[9]:http://www.hubic.com
[10]:http://www.crashplan.com
[11]:http://www.spotify.com
[12]:http://www.nongnu.org/quagga/
[13]:https://www.ansible.com/
[14]:https://github.com/tiernano/whoistozebraconfig
[15]:https://coderbuddy.wordpress.com/2010/10/12/a-simple-c-class-to-get-whois-information/
[16]:http://www.radb.net/
