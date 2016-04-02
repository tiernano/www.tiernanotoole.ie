---
layout: post
tags:
- Web
- Linux
title: Bulk compressing images for the Web
date: 2015-04-29 17:00:00
---
Now that all my sites are running [Jekyll][1] I am trying to get them optimized for **SPEED** which meant
looking at all the stuff that takes time to download... There are more tweaks (and possibly posts) coming down
the road, but to start, I needed to look at images.

First things first. I'm running this on a [Sabayon Linux][2] box, so some of the install commands will be different... (Also, i do need to explain why I moved from Windows to Linux on the [GodboxV2][3], but that's a different post...)

First, install [OptiPNG][4] (they have a Windows build too...) and [JPEGOptim][5]

    sudo equo install optipng
    sudo equo install jpegoptim

[UPDATE] I tried this on an Ubutnu Box, and to install both of these, the package names are the same. so, to install both:

    sudo apt-get install optipng jpegoptim

Next, using the Linux find command (this should work also on OSX...) run OptiPNG and JPEGOptim on all pngs and
jpgs in your given directory:

    find . -iname "*.png" -exec optipng {} \;
	find . -iname "*.jpe?g" -exec jpegoptim {} \;

depending on how many images (and how fast your machine is) it should take a min or two...

That's it! I did a git status, which showed me all the changed images, and then deployed the Jekyll sites... All
good! That's it!


[1]:http://www.jekyllrb.com
[2]:http://www.sabayon.org
[3]:http://tiernanotoole.ie/Computers/GodBoxV2.html
[4]:http://optipng.sourceforge.net/
[5]:http://www.kokkonen.net/tjko/projects.html
