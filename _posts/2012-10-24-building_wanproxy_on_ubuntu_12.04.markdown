---
layout: post
tags:
- Linux
- Networking
title: Building WANProxy on Ubuntu 12.04
date: 2012-10-24 14:28:07
---
[Updated 2016/04/09] I had to use this today to build on Debian 8.3 for 2 different boxes. So, making minor changes (url to git proxy, and where you build from) to make sure this works now.

I have been looking into [WANProxy][1] for a while now, but never successfully got it to build... I have been more successfull reciently, so here is what you need to do.

** NOTE **: I built this on Ubuntu 12.04, so these are the tips for that... Not sure about other Distros...
** Second NOTE ** : I am using the [Digows GitHub Repo][2] for downloads... There is also the [WANProxy SVN Server][3] and their official [downloads page][4]. 

    sudo apt-get install build-essential git-core libssl-dev uuid-dev
    
    git clone https://github.com/wanproxy/wanproxy.git
    
    cd wanproxy/programs/wanproxy
    
    make


*  Note -: git-core is needed to checkout code, build-essentails gives you your essential build utils, and the -dev files are needed for the build
*- NOTE -: I have tried it on a couple VMs and they take about  5 min to build... If you are building on Physical hardware, it may be faster. Also, as a general note, if you are building with multiple processors, try add the -jX option, where x is your CPU count +1. for example, make -j5 if you have CPUs or Cores. or make -j17 if you have 16 cores... 

    cp wanproxy ~/local/bin 

~~Now, this is, so far, as far as i have gotten... but given its building, and its further than I was a few weeks back, i though i would post incase i can help someone else... ~~

** UPDATE ** I have successfully managed to get a WANProxy working. The way i have it setup is as follows:
** UPDATE 2016 ** as part of my series on [getting double internet speed][7], I am back looking at WANProxy... more on that later..

* Linux box in house, and VM on laptop.
* both have WANProxy installed
* use the ** Proxying over SSH ** example [from the WANProxy examples site][6] which shows you how to proxy a single web server over SSH. 
* in my case, i pointed the port at my proxy server inhouse. I also changed the if0.host address from 127.0.0.1 (only accessable from that machine) to its internal IP address (can be seen by anyone on that network)
* finally, I told my browser to use the WANProxy ip and port 3300 (see the if0 config section) as its proxy. 

Works grand so far. no idea yet if its "faster" but its working, which is a start...

[1]:http://www.wanproxy.org
[2]:http://github.com/diegows/wanproxy
[3]:http://wanproxy.org/svn/trunk
[4]:http://wanproxy.org/get.shtml
[5]:https://github.com/diegows/wanproxy/issues/1
[6]:http://wanproxy.org/examples.shtml
[7]:https://www.tiernanotoole.ie/tag/Projects/
