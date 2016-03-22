---
layout: post
tags:
- RouterOS
- Networking
- IPv6
title: IPv6 Firewall rules for MikroTik RouterOS
date: 2012-12-20 11:09:06
---
After [yesterday's post on IPv6 Networking in the house][1], I realized that all machines internally had publically facing IPv6 addresses! I started to panic, then went looking online, and found the following script:

<script src="https://gist.github.com/4344701.js"></script>

This script, when run on your RouterOS board, will allow Established and Related connections, allow outgoing connections, and drop anything incoming that has not been requested... so, now everything inside the network should be more secured... I am new to this IPv6 stuff, so I am still learning... but, i am getting there...

[1]:http://tiernanotoole.ie/2012/12/19/ipv6_%2B_mikrotik_%2B_linux_%2B_windows.html