---
date: 2016-11-02T00:00:00Z
published: true
tags:
- Docker
- Development
title: Building Jekyll sites with Docker on Windows
slug: building-jekyll-sites-with-docker-on-windows
---

As some of you probably know (or based on the footer of the site) this site is built with [Jekyll][1]. Jekyll is a static web site builder, written in Ruby, and is a bit of a pain to build on Windows. Earlier on this year, I [wrote up a post][2] explaining how to use Jekyll on Windows using Bash on Ubuntu on Windows... It was a bit complicated, and, well, worked a few times, but was not too successfull... So, were do we go next? Well, [Docker][3] to the rescue!

I am running the [Windows 10 Anniversary edtion][4] witch has [container][5] and [docker support][6].  using the [repo for this site][7] and the scripts (specifically [build-tiernanotooleie][8] and [geekphotographer.com][9]) i can build the docker site on my local Windows machine and upload the sites as required (I host on [NFSN][10] and upload via [RSync][11]). The docker image i build from is a Linux docker image, do i need a Linux container running (and the docker tooling). I also use Bash on Ubuntu on Windows to upload using RSync. All is going well so far...

[1]:https://jekyllrb.com/
[2]:https://www.tiernanotoole.ie/2016/04/11/installing-jekyll-on-bash-on-ubuntu-on-windows.html
[3]:http://www.docker.io
[4]:https://blogs.windows.com/windowsexperience/2016/08/02/how-to-get-the-windows-10-anniversary-update/
[5]:https://msdn.microsoft.com/en-us/virtualization/windowscontainers/quick_start/quick_start_windows_10
[6]:https://docs.docker.com/engine/getstarted/step_one/
[7]:https://github.com/tiernano/www.tiernanotoole.ie-docker
[8]:https://github.com/tiernano/www.tiernanotoole.ie-docker/blob/master/build-tiernanotooleie
[9]:https://github.com/tiernano/www.tiernanotoole.ie-docker/blob/master/geekphotographer.com
[10]:http://www.nearlyfreespeech.net
[11]:https://en.wikipedia.org/wiki/Rsync