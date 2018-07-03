---
title: Playing with AMD's Epyc
date: 2018-07-02 21:00:00 +0000
publishdate: 2018-07-02 20:00:00 +0100
tags:
- Hardware
- Programming
- Reviews
layout: post
published: true
---
So, a few days back I got an email from [Packet.net](http://www.packet.net) about a promotion they and AMD where running. Essentially, they gave me some credit for their service (i am an existing customer) to play with one of their [c2.medium](https://www.packet.net/bare-metal/servers/c2-medium-epyc/) machines. A c2.medium comes with an [AMD EPYC 7401P](https://www.amd.com/en/products/cpu/amd-epyc-7401p) which consists of 24 physical cores clocked at 2Gz with an all core boost at 2.8Gb and a max clock of 3Gz, 48 threads, 64GB ECC Memory, 2x120GB SSDs for boot and 2x480GB SSDs for main stoage. It also has a 20Gb network link (2x10gb bonded) and can run pretty much any OS you can think of (Windows is not on the list officially, but you can boot off your own ISO, so you could probably get it on there... might not be supported, but it might be possible). all this for $1 per hour! And did i mention they are bare metal machines?

This was the perfect opportunity to play with the new AMD processors. My current and previous generation workstations ([GodBoxv1 ](https://www.tiernanotoole.ie/Computers/godbox.html)and [Godboxv2](https://www.tiernanotoole.ie/Computers/GodBoxV2.html)) are both running Intel Xeon processors. the machine previous to this, the mac pro, is also running a Xeon processor. But previous to both of them, my first 2 major workstations ran AMD... the first ran 2 AMD Athlon MP processors. These were old school processors that had a single core, and i cant even remember their speeds, but i do know there were 32bit only and the machine maxed out at about 1.25GB RAM (well, i had it maxed out at that). the second AMD workstation ran 2 AMD Opterons... again, single core processors, but this time, they ran 64 bit and IIRC maxed out at 8GB ram. This was a limitation of the board, not the processor...

I have been thinking about GodboxV.next, and the AMD processors, specicially the [Threadrippers](https://products.amd.com/en-us/search/cpu/amd-ryzen%E2%84%A2/amd-ryzen%E2%84%A2-threadripper) and Epycs, are contenders for the next machine... so, this test allows me to check them out before i buy!Why would i say no?!

So, i spun a box up in New Jersey running Ubuntu 17.10 to play with it, and here are my findings...

First, i ran lscpu on the box to see what i was playing with:

<script src="https://gist.github.com/tiernano/4877abe19c89f1e45e617da1b4d46447.js"></script>

I then ran _fdisk -l_ to see what disks i had to play with. on my machine sda and sdb where the 480gb SSDs, sdc was a 120gb that was empty and sdd was the boot drive... i installed the _btrfs-progs_ and then formatted sda and sdb as a RAID0 array, which i then mounted to /mnt. this gave me just under 900gb to play with...

So, my first test is the usual test: building the Linux Kernel. I know that this is something that the lads at [ServeTheHome](http://www.servethehome.com) do a lot but its something i wanted to try my self... So, first i installed git and build essential, then bison, flex and ncurses-dev, then i cloned Linus' git repo at [_git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git_](git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git). First things first: this machine has a twin 10gb link, a shed load of cores and some very fast storage. How long did it take to clone? it download 1.02 GiB at 35.32MiB/s (about 30 seconds and about 280Mbit/s) and all in, took 2 min 55 seconds to clone. I then ran 'time make -j 49' to see how long it would take... hmm... no config file... make menuconfig and just hit save... defaults are grand... time make -j 49 again... and more errors... after a bit of googling, i find the page from Ubuntu [showing what i need to do to build the kernel](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild). i follow that... download a LOT more stuff using their instructions, and finally, we get to build... Time: 6 min 12 seconds... this is a FULL default build of the kernel...

![](/uploads/2018/07/03/top_kernel_build_epy_hdb0R.jpg)

Same build on a VM on GodboxV2 (which was given 32GB RAM and 16 thread, so a full Xeon E5-4620) took 8 min 27s to clone (8.18MiB/s. or about 64Mbit/s) and 36 min... yea, that is 3x less cores, 2x less memory, slower storage (This is on Spinning Disk, not SSD), slower network and it is also a VM VS bare metal, still, to be essentially 6 times slower? interesting... I might, at some stage, boot the machine off a live Linux USB and run some more tests, but not tonight...

![](/uploads/2018/07/03/top_kernel_build_god_lwcxo.jpg)

So, all this is because i was holding out for the main event... Photo processing... I wanted to do something "real life", which for me would be development and photo processing... the kernel build gives an idea of a large project build built, the image processing gives an idea of multimedia work...

so, i devised a test: Export a bunch of photos (mix of photos taken on my 5Ds, 5D MKII, iPhone 6 Plus and iPhone 7Plus) that are stored in light room as full  and run them though a basic .NET Core app i wrote. the code for the app is [available here](https://github.com/tiernano/imageresizer-testapp). The app fully utilizes the machine by using multiple threads, and because its 64 bit, it will use as much memory as it can get its hands on. It just does some basic processing: open the file, resize to 1024X1024 and then save it... the 1024X1024 part is just a test... i was a bit under the gun on time, so couldnt spend as much time working on it as i wanted to...

In total, there was 1546 photos exported, and the total file size was 15Gb. First obstical was to get them uploaded to the Packet machine, which took a while (my upload speed is currently 40Mbit/s)... Once up, i downloaded a copy of dotnet core 2.0 SDK, cloned the repo with the project, built and ran... and man, its fast! **4 min 43 seconds**. And it used all the cores.

![](/uploads/2018/07/03/image_resizer_epyc.jpg)

Running the same code on GodBoxV2 on the bare metal (no VM this time), i got **17 min 35 seconds** of a run... 4 times slower! Now, GodBoxV2 has other things running in the back ground, but not that much... I also noticed that, on average, photos were being processed in 3-5 seconds on Epyc, but nearly 13-15, and sometimes 20 and 25 seconds on GodBoxV2. I also noticed that on Epyc, the dotnet process took nearly 45GB of RAM... to run... On GodBoxV2, it took over 70!

![](/uploads/2018/07/03/image_resizer_godbox_f5de0.jpg)

So, there you have it. Some starting tests with these processors. I am well impressed with these processors, and would have no issue getting one for the next GodBox... And with names like Epyc and Threadripper, why not?!