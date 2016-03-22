---
layout: post
tags:
- Camera
- Photography
- Hardware
- Raspberry Pi
title: more raspberry pi and camera antics
date: 2012-10-12 15:13:53
---
A while back I [posted][2] about the [Raspberry Pi][3], and in the post was a link to a Photographer who was [embeding a Raspberry Pi into a Canon 5D MKII battery grip][4]. Well, its been a while, and i have been thinking about the Pi and Cameras, so I went looking around... Here is what i found.

* [HDR Photography with a Raspberry Pi and GPhoto2][5]: It was linked at the end of David's post, and i missed it completely. David mentions he was using [GPhoto2][6] to take photos from the Pi, so its a good place to start.
* [GPhoto2 and the Raspberry Pi][7]: starters guide on getting the Pi to talk to your Camera.
* Not specifically Pi+Camera released, but the [Stackoverflow Raspberry Pi Page][8] is a handy resource for asking questions...

The one thing i have not been able to figure out is how to tell the Pi to take the photos out of the camera **wihtout having a monitor plugged in**. I was thinking either tell it, on boot, to start monitoring the camera and download everything. This way, if you have it plugged into a external power source, it will be monitoring and downloading to somewhere... USB HDD, USB Key, etc. If there is a Wifi spot around, try uploading them to a location, posibily manageable via web interface of some sort... Lots of interesting ideas can be done... its just a matter of doing them... :)

[1]:http://islandinthenet.com/2012/08/23/hdr-photography-with-raspberry-pi-and-gphoto2/
[2]:http://tiernanotoole.ie/2012/09/06/Rasberry-Stuff.html
[3]:http://www.raspberrypi.org/
[4]:http://davidhunt.ie/?p=2641
[5]:http://islandinthenet.com/2012/08/23/hdr-photography-with-raspberry-pi-and-gphoto2/
[6]:http://gphoto.org/proj/gphoto2/
[7]:http://skowron.biz/artikel/gphoto-raspberry/
[8]:http://raspberrypi.stackexchange.com/