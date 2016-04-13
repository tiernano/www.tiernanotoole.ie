---
layout: post
tags:
- Networking
- Sophos UTM
- Hardware
- HomeLab
- Ubiquiti
title: Edge Router, Sophos UTM, DMZ and LAN Networks
date: 2015-09-30 20:00:00
---

I have been using an [EdgeRouer POE][2] as my main router for most of the network (some of the network still uses [PFSense][1] as a router, but thats being removed soon) for the last few weeks, and i am quite happy with it. I also have a second router, a [Sophos UTM][3] VM between my first LAN (essentially a DMZ) and my client LAN (there will be more "LANs" over there soon). The Client LAN is NATed between the DMZ and the LAN, which means anything on the LAN i want to access from the DMZ has to be port forwarded... Ideally, not much from the LAN should be accessible though the DMZ, but in my initial setup, stuff like [Plex][4], etc, is...

What i wanted to do was setup a proper firewall between both networks, without the use of NAT... Do do this, i first had to disable th masquerading rules in Sophos:

![Masquerading Off](https://www.tiernanotoole.ie/post_images/2015/09/30/20150930-masquerading-off.png)

next, on the EdgeRouter, i added a static route to point at the new network:

![static route](https://www.tiernanotoole.ie/post_images/2015/09/30/20150930-static-route.png)

And finally, under firewall rules, i allowed what i wanted to allow (in this case, SSH from any DMZ client (not advised) to my Mac Mini).

![firewall rules](https://www.tiernanotoole.ie/post_images/2015/09/30/20150930-firewall-rules.png)

And that, as they say, is that! So far, so good!

[1]: http://www.pfsense.org
[2]: https://www.ubnt.com/edgemax/edgerouter-poe/
[3]: https://www.sophos.com/en-us/products/unified-threat-management.aspx
[4]: http://www.plex.tv
