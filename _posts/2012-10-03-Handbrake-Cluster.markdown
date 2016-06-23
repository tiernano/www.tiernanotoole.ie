---
layout: post
title: Handbrake Cluster
tags:
- Programming
- Projects
- Media Center
---
[UPDATED] someone asked in the comments if there was an binary build for this file. there is now! [http://handbrakecluster.codeplex.com][8] now hosts the code and binaries, and will soon have help files and documentation. 

A few days back, i wrote a post titled [Powershell + Handbrake + AppleTV + iTunes = Automatic TV... ish][1]. In it i included a block of Powershell code to bulk convert TV shows from whatever format you had them in to a M4V format for the AppleTV. Well, as they say "If necessity is the mother of all invension, lazyness must be the father". I have a lot of shows i wanted converted to the AppleTV, so i built something... Its called [HandBrake Cluster][2] and is written in [.NET 4.5][3], uses [MSMQ][4] and [Handbrake][5] to do the processing... The workflow is as follows:

* setup the system as described on the [HandBrake Cluster][2] site.
* run the adder program with the paramaters required (location of files you want converted, type of files to find, where you want the files to be placed, output file type)
* run the cluster EXE on as many machines as you want. each machine will need to point to the correct MSMQ on the head node, have their own copy of Handbrake, and must have access to the fileshare that you are reading and writing to...
* each node will take a message of the queue, process the file and then mark it as completed. There is code to see if the message has failed, so, in theory, if something goes into the queue, it should always be processed... 

I have run this at home on a couple of different machines, and so far so good... my room gets a bit warmer when i kick this off, and between the 3 machines i ran it on, my FPS count went from just 80-120 on the Godbox, to a total of about 160 - 240 FPS (Godbox = 80-120, Server 1 and 2 are about 40-60FPS). 

The next thing i managed to do was tweak my import process for iTunes. I am using a program called [iHomeServer for iTunes][6] which is running on the [GodBox][7]. It monitors a folder, which is where [HandBrake Cluster][2] is writing to, and adds them to iTunes. I can then tweak the metadata using the tool, so i can add art work, tell it which shows are related, and it sets up Art work, title info, etc. It is very handy, and something i am very happy with. 

[1]:https://www.tiernanotoole.ie/2012/09/28/Powershell-HandBrake-AppleTV-iTunes.html
[2]:https://github.com/tiernano/HandbrakeCluster
[3]:http://www.microsoft.com/en-us/download/details.aspx?id=30653
[4]:http://msdn.microsoft.com/en-us/library/aa967729.aspx
[5]:http://handbrake.fr/
[6]:http://www.bizmodeller.com/iHomeServer_for_iTunes.aspx
[7]:https://www.tiernanotoole.ie/Computers/godbox.html
[8]:http://handbrakecluster.codeplex.com
