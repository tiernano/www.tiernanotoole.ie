---
layout: post
title: PowerShell + HandBrake + AppleTV + iTunes = Automatic TV... Ish...
tags:
- Powershell
- Guide
- Media Center
---
I have an [AppleTV][1] in the house (3, actually) and i am very happy with its ease of use, size and cost... You cant really argue with the small price! 

I also have a lot of content that works great with the AppleTV in iTunes, but i have content which does not work so great with the AppleTV... So, i needed to find a way to convert files quickly and easily... thats where PowerShell and [Handbrake][2] come in... 

{% gist 3798509 %}

* in the code above, you need to set the path of where your files live. in my case they live on a NAS.
* next, set the location of HandBrake... i have a 64 bit copy of Windows, and a 64 bit copy of HandBrake. 
* set the new file name to where you want the file to go. in my case i have it set to my "[Automatically Add to iTunes][3]" folder, which is a magic folder for iTunes that copies any files dropped in there to your iTunes library. 
* finally, conversion is run...

This may take a few min, depending on a few factors:

* how many files you are converting
* how fast your machine in
* how fast your machine can read and write the files...
* etc...

I have set files to convert on 3 different machines (the GodBox and 2 other servers) and i am getting speeds of anywhere between 250FPS (on the GodBox running 2 instances of HandBrake CLI) and 40 - 60 FPS on the older servers... on the remote machines, they are sending files to the GodBox folder also, so once everything completes, its just a matter of opening iTunes and we are good to go... Now to figure out how to automate the Metadata import... 



[1]:http://www.apple.com/appletv
[2]:http://handbrake.fr/
[3]:http://support.apple.com/kb/HT3832