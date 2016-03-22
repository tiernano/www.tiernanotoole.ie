---
layout: post
tags:
- OSX
- Networking
- Tips
title: enabling VNC from SSH on OSX
date: 2012-11-29 16:16:49
---
I have a [Late 2008 MacBook Pro][1] in the house, and SSH is enabled on it. I usually leave it on when in work. Anyway, SSH is enabled, but VNC access is not... I found the following command on [Ryan's Tech Notes][2] allowing you to enable it though SSH:

{% gist 4170122 %} 

** NOTE ** Change *mypasswd* to your own password!!!

If you need to disable it, use the following:

{% gist 4170129 %}

Also, of note, I am using [RealVNC client for Windows][3] to connect. 

[1]:/Computers/MacBookPro.html
[2]:http://technotes.twosmallcoins.com/?p=279
[3]:http://www.realvnc.com/