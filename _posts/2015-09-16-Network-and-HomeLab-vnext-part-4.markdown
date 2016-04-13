---
layout: post
tags:
- Networking
- PFSense
- Hardware
- HomeLab
- Ubiquiti
title: Network and HomeLab V.Next (Part 4)
date: 2015-09-16 14:15:00
---
So, after some messing, tweaking, and thinking, I have made some progress with the home lab... or at least broken some stuff... I mentioned previously that i had a [Ubiqititi networks EdgeRouter POE][1] in the home lab. Originally, the plan was to use a Virtual [PFSense][3] box for my core router... Given the power usage of the current PfSense Box (I have 2 [MPower Pro][2]'s watching power in the lab) I am now thinking of moving to just the EdgeRouter for, well, edge routing...  below is the usage of the ProLiant for the last 12 hours or so:

![Proliant Power Usage](https://www.tiernanotoole.ie/post_images/2015/09/16/20150916-proliant-power-usage.PNG)

for the same period, here is the usage for the [Edge Router][4]:

![EdgeRouter POE Power Usage](https://www.tiernanotoole.ie/post_images/2015/09/16/20150916-edgerouter-power-usage.PNG)

I am also setting up a DMZ for front facing services, and then a LAN for inside facing machines. There will be a firewall (currently thinking [Sophos UTM][5] or similar) between the DMZ and the network. Some machines will be able to access the DMZ, and there may be machines allowed into the LAN, but only some things... not even sure if that would be done...

I also need to work out the VLAN side of things. I have currently though of the following VLAN setup:

* WAN 1 (connected directly to the Cable modem)
* WAN 2 (again, direct to cable modem)
* LAN Network
* DMZ Network
* VoIP Network
* IOT (stuff for running the house, like [Nest][6], the MPower devices or the like)
* Media Network (Plex, Roku, Apple TV, Chrome Cast, etc. Not sure if i need to separate this, but it might be done...)

The current [Cisco 3560G switch][7] should do all that, without problems, so no new switch needed... lets see what i can break over the next while...

[1]: https://www.tiernanotoole.ie/2015/08/05/Ubiquiti-EdgeRouter-POE-In-the-lab.html
[2]: https://www.ubnt.com/mfi/mpower/
[3]: http://www.pfsense.org
[4]: https://www.ubnt.com/edgemax/edgerouter-poe/
[5]: https://www.sophos.com/en-us/products/unified-threat-management.aspx
[6]: https://nest.com/ie/thermostat/meet-nest-thermostat/
[7]: http://www.cisco.com/c/en/us/products/switches/catalyst-3560-series-switches/index.html
