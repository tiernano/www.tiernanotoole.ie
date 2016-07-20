---
layout: post
title: "Meraki and Ubiquiti networks gear Update"
tags: 
  - Networking
  - HomeLab
date: "2016-06-20 08:00"
published: true
---

In [part 6][1] of my [Double Internet Series][2] I mentioned i was running a [Meraki][3] [MX64][4] in the network, and said i would write up about it. I am taking this oppertunity to also write up about the [Ubiquiti networks][6] gear in the house also.

* First on the list is my older [Ubiquiti Edgerouter POE][5]. It currently in the process of being decommissioned, or used for something else. It was the main edge router for the network: it had both internet connections connected, and did routing, firewalls, etc, but with the [Proliant][12] taking over as a router, it is not requried as much any more... Its still on, mainly because its still a DHCP server, but not much else.
* There are 2 [Meraki MS220-8][7] switches next. [GodBox1][9] and [Godbox2][10] both connect in here, and are bonded, as is everything else on the network. The MS220-8 has 8 GigE ports, but also has 2 SFP ports. I bought 4 SFP Ethernet adapters and have a short calbe running between the switches. That uplink is also bonded. All going well so far!
* All meraki hardware can be managed though the meraki dashboard. check out their site for more details and examples of how to use it.
* I bought one of the MS220's from ebay a few months back, and loved it. Then i realized that you can get your hands on free gear, the MX64, an MS220 and a Wifi Access point if you attend their [webinars][15]. Terms and conditions apply, but check them out!
* I have 2 [Ubiquiti UniFi APs][8], one in the front of the house, one in the back. They are connected to one of the MS220's, but dont work with its POE (maybe the EdgeRouter could do that, since its POE...) so there are injectors for them. Anyway, the network ports on there are VLANed to the MX64 (more on that later) and the detault traffic is going to a management VLAN.
* The [MX64][4] has a static internal IP on my DMZ network, and uses the Proliant as an upstream connection. Upstream on the [Hetzner][11] server, all traffic coming from the MX64 ip uses one of my /29 ip block. all traffic to that ip is also forwarded directly to the MX64.
* I has 2 small, unmanaged switches (a cheap 8 port Linksys and a 8 port TP Link) which are used for seperate things: the Linksys has 4 Raspberry Pi's, which run a [GlusterFS] cluster, plugged into it and the TP Link connects to my printers.
* I also have a [Mikrotik CRS226-24G-2S+IN][13] which has 2 10Gbit SFP+ Ports, and plan on using this for higher speed networking soon, aswell as a [Cisco 48 port 3560][14] which also has 4 SFP ports (GigE) and may come in handy for something soon...

So, thats the network currently. any questions, please leave a comment.

[1]:https://www.tiernanotoole.ie/2016/05/17/double-speed-internet-part-6-hetzner-edition.html
[2]:https://www.tiernanotoole.ie/tag/Double%20Internet/
[3]:https://meraki.cisco.com/
[4]:https://meraki.cisco.com/products/appliances/mx64
[5]:https://www.ubnt.com/edgemax/edgerouter-poe/
[6]:http://www.ubnt.com
[7]:https://meraki.cisco.com/products/switches/ms220-8
[8]:https://www.ubnt.com/unifi/unifi-ap/
[9]:https://www.tiernanotoole.ie/Computers/godbox.html
[10]:https://www.tiernanotoole.ie/Computers/GodBoxV2.html
[11]:http://www.hetzner.de/en
[12]:https://www.tiernanotoole.ie/Computers/proliantml110.html
[13]:http://routerboard.com/CRS226-24G-2SplusIN
[14]:http://www.cisco.com/c/en/us/products/switches/catalyst-3560-series-switches/index.html
[15]:https://meraki.cisco.com/webinars