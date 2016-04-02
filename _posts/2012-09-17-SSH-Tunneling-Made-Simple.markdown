---
layout: post
title: SSH Tunneling made simple
tags:
- Linux
- SSH
- Networking
---
Something I do on a regular basis is use the internet while "out and about". This could be college, which has a semi open network, or it could be a coffee shop, which also usually has a semi open connection. There is also the possibility of using the a mobile internet connection on my iPhone, which can be slow, but at least its only shared with me... Anyway, over on RevSys.com, there is a post [SSH Tunneling made simple][1] which shows you how to open an SSH tunnel to your machine somewhere else (could be at home, as is my case, or a VPS/Dedicated server somewhere, or even on Amazon...) and use that for different things... In the case he shows, its for SMTP access. For my case, i am forwarding my local port 3128 to my Microsoft TMG 2010 Server in house on port 8080. Then my system proxy on my laptop is set to use localhost:3128 for all web and HTTPS requests. Very handy. One other tip: Using the -C flag, so your command may look like:

    ssh yourname@remotemachine -L 3128:remoteMachine:8080 -C

will compress data between you and the SSH server, which for basic web browsing (HTML, CSS, JS) will make things faster, but for stuff like images, etc, may not work so well... Your Mileage may Vary...

Also, while on the subject of SSH, Linux Journal has an article on [Eleven SSH tricks][2] which mentions compression, Encryption Cyphers, X11 Forwarding, Config files and other interesting bits.

[1]:http://www.revsys.com/writings/quicktips/ssh-tunnel.html
[2]:http://www.linuxjournal.com/article/6602
