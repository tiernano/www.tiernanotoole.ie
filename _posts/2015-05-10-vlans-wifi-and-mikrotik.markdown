---
layout: post
tags:
- Networking
- RouterOS
- Mikrotik
title: VLANs, Wifi and Mikrotik
date: 2015-05-10 18:40:00
---
About a month ago, while i was recovering from surgery, i attended a Webinar on
[Cisco Meraki][1] devices. After the webinar, i was contacted by Maraki and given a [MR18][2] with a 3 year license, to play with and evaluate. So, i set it up in the house and all was good.

Thing is, the wifi in the house was grand previously. I have a [Routerboard RB951G][3] which does the job and has no issues. And because i am mostly offsite in the office i work, and because i need to remotely manage the network, the MR18 is going into the office from tomorrow morning. I may talk about the MR18 and the rest of the Meraki gear later on, but this is not that post. This post is about something the MR18 did, and i wanted to do on the RB951.

So, the MR18 allows you to create multiple Wifi SSIDs, each with different encryption and security and can use different VLANs. Now, the Mikrotik does the same, but the VLANs stuff is not that easy to figure out. but essentially, what i needed to do was as follows:

create your new wifi SSIDs:

    /interface wireless
    add master-interface=wlan1 name=wlan1.10 ssid=vlan10
    add master-interface=wlan1 name=wlan1.20 ssid=vlan20


next, create your vlans. these need to be connected back to your main
ethernet connection. In the case of my RB951, there are 5 ethernet
ports. 1 is the gateway back to my Cisco switch and on to my [PFSense][4] router. 2-5 are all slaves of number 1, which is a master. So, 1 is essentially a trunk network. So, vlans are created on that.

    /interface vlan
    add name=vlan10 interface=ether1-gateway name=ether1.10 vlan-id=10
    add name=vlan20 interface=ether1-gateway name=ether1.20 vlan-id=20

next, a bridge to connect them

    /interface bridge
    add name=vlan10
    add name=vlan20

and connect them to the bridge

    /interface bridge port
    add bridge=vlan10 interface ether1.10
    add bridge=vlan10 interface wlan1.10
    add bridge=vlan20 interface ether1.20
    add bridge=vlan20 interface wlan1.20

And thats all i needed to do. I have a [Sophos UTM Home edition][5] running on a vm for testing, which vlan10 is connected to. It has an upstream connection back to the PFSense box, which has it firewalled off and allows it outside the network, not nothing else. I am planning on doing this with other firewalls, just to do some testing with. This allows me to connect my phone or laptop, or any other wifi device, to a given wifi connection and then be on my way. I also have an older Dell PowerConnect switch, which, if i ever get around to it, will have multiple connections back to the Cisco and then allow physical devices to connect to different vlans.

Any questions, comments, etc, leave a comment blow.

[1]:http://www.meraki.com
[2]:https://meraki.cisco.com/products/wireless/mr18
[3]:http://routerboard.com/RB951G-2HnD
[4]:http://www.pfsense.org
[5]:https://www.sophos.com/en-us/products/free-tools/sophos-utm-home-edition.aspx
