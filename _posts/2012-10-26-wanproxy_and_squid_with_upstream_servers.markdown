---
layout: post
tags:
- Networking
- Linux
title: WANProxy and Squid with Upstream Servers
date: 2012-10-26 13:14:00
---
In my [previous post on WANProxy][1], i did not really go into detail about what it actually was. The direct quote from their site is *[WANProxy][2] is a free, portable TCP proxy which makes TCP connections send less data, which improves TCP performance and throughput over lossy links, slow links and long links. This is just what you need to improve performance over satellite, wireless and WAN links.* This is something that has interested me for a while, so i have been looking into it, and so far so good... In my last post i mentioned i was proxying [Squid][3] traffic, in todays post, i still am, but with some tweaks.

* i have a Squid box running in the house. It is connected to 2 Cable Modems, giving me 250Mbits/s down and 20Mbits/s upload connection. It is caching data locally also.
* on my laptop i have Squid running also. It connects to a WANProxy server at home and proxies the Squid server. The local squid box is using the home Squid box as an upstream connection.
* for upstream connections i used the following lines in the squid.conf:

{% gist 3958472 %}

I have set it to never use a direct connection, which is probably silly, since if i loose the WANProxy connection, i loose connectivity... Also, port 3300 is the WANProxy port its listening on. 

So far, so good... I am also thinking this could be an interesting thing to get working on a [Raspberry Pi][4].... Just a though... :)

[1]:http://tiernanotoole.ie/2012/10/24/building_wanproxy_on_ubuntu_12.04.html
[2]:http://www.wanproxy.org
[3]:http://www.squid-cache.org
[4]:http://www.raspberrypi.org