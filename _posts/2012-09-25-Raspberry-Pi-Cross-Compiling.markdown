---
layout: post
title: Building a Cross Compiler for your Raspberry Pi
tags:
- Raspberry Pi
- Programming
---
My main machine at home, known as "The GodBox" is a Dual Processor, [Quad Core Xeon 5520][3] with 60Gb RAM, 2 [300Gb 10,000 RPM Western Digital Velociraptor][4] in RAID 0 for boot, 4X1Tb 7200RPM drives for storage, 2 more 300Gb 10,000 RPM drives for "scratch disk" and a couple high(ish) end graphics cards with 3 monitors plugged in... Hence the name, GodBox!

Anyway, The [Raspberry Pi][2], on the other hand, has a 700Mhz processor, 256Mb RAM and not much else... So, if you need to write code for your Pi, and you don't want to wait a long time to compile, check out this tutorial on [how to build a cross compiler for your raspberry pi][1] which will allow you to build your apps on a different machine... I have a college project which the Raspberry Pi will be used for, and i am thinking this will be how i build code. 


[1]:http://www.bootc.net/archives/2012/05/26/how-to-build-a-cross-compiler-for-your-raspberry-pi/
[2]:http://www.raspberrypi.org/
[3]:http://www.amazon.com/gp/product/B001QCEMFA/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B001QCEMFA&linkCode=as2&tag=lotassmartmann00
[4]:http://www.amazon.com/gp/product/B005CGDSDI/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B005CGDSDI&linkCode=as2&tag=lotassmartmann00
