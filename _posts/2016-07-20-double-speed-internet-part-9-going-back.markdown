---
layout: post
title: "double speed Internet Part 9 - Going Back"
tags: 
  - Guide
  - Networking
  - IPv6
  - Projects
  - HowTo
  - HomeLab
  - Double Internet
date: "2016-07-20 12:00"
published: true
---

[NOTE] This part 9 in a series of posts. The rest can be found [here](https://www.tiernanotoole.ie/tag/Double%20Internet/)

Well, the double internet experiment is about ready to be finished... After 9 posts, 4 months, lots of sweating, many painful nights trying to figure out why something stopped using, shouting when [Netflix][1] did not work, wondering why my internet connection was so slow, and many, many other problems, i have decided to wind down the project. in the last 9 posts, i have learned a lot, and i hope i have helped someone figure out some stuff on their end. Even though this is a wind up of the project, there are still new things i have to share.

* I found another project that has potential for speeding up the internet: [VTrunkd][2]. after some testing, i does seem to manage to speed up the connection, but either limits on hardware i have in house, or limits of hardware in the cloud, or even the software, stopped me in my tracks... i did see 400mb/s out of it at one stage, using 200mb/s from each modem... its close, but its not the full 720...
* messing with [Quagga/Zebra][4] as mentioned in [the previous post][3] has been, well, interesting... I did manage to get all [OVH][5] traffic sent though their server, [Digital Ocean][6] traffic sent over that box, and everything else over [Hetzner][7]. I added an [Azure][8] box to the mix for a while, aswell as a [Vultr][9] box, but it got very messey, very quickly. if i had something automated, it would be better.
* the idea of having a /29 IP range in [Hetzner][7] and forwarding it though the tunnels back to the house did work. My [Meraki MX64][10] had one IP address, i had a mail server on a second, everything else on a third, and was planning on using more... but its just, well, again, messy. So, i will be going back to the idea of 2 IP addresses, and hoping whatever i put infront of the network can figure stuff out...

So, what am i moving to? well, thats a question... Currently, i have the [Meraki MX64][10] plugged directly into the modems, and protecting my LAN. So far, so good, but due to hardware limits, it maxes out at around 260mb/s. So, thats out of the question for the main network! I did at one stage have [Sophos UTM Home edition][11] running. Sophos also have their [XG firewall][12] available for home use, so i might try that... There is also [PFSense][13] which i used before also... And there may be more... Maybe there will be a new series reviewing these home firewalls? we will see...

[1]:http://www.netflix.com
[2]:http://www.vrayo.com/how-to-set-up-a-bonding-vpn-connection-in-linux/
[3]:https://www.tiernanotoole.ie/2016/06/08/double-speed-internet-part-8-routing-around.html
[4]:http://www.nongnu.org/quagga/
[5]:http://www.ovh.ie
[6]:https://m.do.co/c/d4d345b83b55
[7]:http://www.hetzner.de/en
[8]:http://www.azure.com
[9]:http://www.vultr.com/?ref=6925433
[10]:https://meraki.cisco.com/products/appliances/mx64
[11]:https://www.sophos.com/en/products/free-tools/sophos-utm-home-edition.aspx
[12]:https://www.sophos.com/en-us/products/free-tools/sophos-xg-firewall-home-edition.aspx
[13]:https://www.pfsense.org/