---
layout: post
tags:
- Networking
- VMWare
- PFSense
title: PFSense with Multiple Public IPs
date: 2015-05-30 18:50:00
---
So, a few weeks back, i got my hands on a [Hetzner][1] Dedicated box. It has a quad core Xeon, 32Gb ram, 3x3Tb hdds, RAID controller and KVMoIP. one of the first thing i did was get myself a /29 IP pool (8 total, 6 usable IPs). There where already 3 IPs given to me: 1 for the KVM, one for the box itself, and 1 as the router for the IP block.

So, i need to setup my own router, so i picked [PFSense][2] since its what i run in house. I gave it 2 network connections: 1 connected to the main network adapter on the VMWare ESXi box (public) and one to a virtual switch, which is only used by VMs. The public is the WAN link and it gets a static IP from Hetzner, and the virtual switch is then my "LAN" link. This allows me to have standard NATed network connections to any VM i have, but then, what do i do with those IPs?

So, after a lot of digging, i found the answer. So, this should help.

* Under firewall, click on Virtual IPs.
* click the plus. I then selected IP alias, selected the WAN interface and set the IP to my first public IP i wanted to give. in my case, i was given a /29 block, and my first address was 176. This is the network address. I used 177. Likewise, my last address is 183, but that cannot be used either as its a broadcast address. give it a description and then hit OK. Repease for all IPs you want to use. TIP: Give each a meaningful description!
* Next, click firewall, NAT and 1:1. Click the add button and select your interface as WAN. set the External Subnet IP as the one you want to use and your internal IP as the machine that will have it. Thats all i did on that screen...
* Then go to Firewall, NAT, outbound... this is where things got complicated. Set the mode to "Manual outbound NAT rule generation (AON - Advanced Outbound NAT)" and click save.
* Then create a new rule: Interface: WAN, Source, Network, IP of the internal machine and then under translation, under address select the IP you want to give it. If you followed my tip in step 2, you should see the descriptions in here.

After saving everything and reloading the firewall, visiting a page like [WhatsMyIP][3] or [ICanHazIP][4] should show you your public IP. You can then create firewall rules to allow access. Quick idea would be:

Firewall/Rules, Add, Interface WAN, Destination: Local IP you want to use, and give whatever "normal" rules you would (HTTP, lock down to source address, etc). Click apply and hitting that address using what ever method (SSH, HTTP, etc) should work.

YMMV, but hopefully this helps! Any questions, leave a comment.

[1]:http://www.hetzner.de/en
[2]:http://www.pfsense.org
[3]:http://www.whatsmyip.org
[4]:http://icanhazip.com
