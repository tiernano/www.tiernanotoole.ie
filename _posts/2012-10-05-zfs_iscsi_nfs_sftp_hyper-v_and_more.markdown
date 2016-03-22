---
layout: post
tags:
- ZFS
- Storage
- Projects
- Hyper-V
title: ZFS iSCSI NFS SFTP Hyper-V and more
date: 2012-10-05  9:38:13
---
As part of my new task to make my files safer and backups faster, and, well, cheap, I am looking into [ZFS][5] for my storage needs. My needs are as follows:

* Allow me to store lots of different types of data (Photos, Videos, Music, VMs) in different formats (RAW and JPG photos, MP4, AVI and DivX Videos, with DVD and BluRay rips also a posibility, MP3 music and VHD files from HyperV, inclduing ISOs and Snapshots). I also need to store different file systems using [iSCSI][6] (Mac and Windows clients will be mounting the storage). 
* must be safe. DO NOT LOSE DATA!
* must be somewhat fast. I have VHDs weighing in at 100Gb... my photo collection is 600Gb. If i need to move or copy files to the storage system, it must be fast.

So, ZFS offers all these features. I can export a file share as iSCSI, NFS, SMB, etc. All works well. But the replication stuff is the interesting part...

The plan, which i am working on, is as follows:

* have 2 machines setup: one in house and one in a datacenter (I have a dedicated box in the [Hetzner][1] data center). both could be VMs (the one in the datacenter will more than likley be a VM).
* use the storage on the local system for whatever i need backed up. 
* have a script which will take a snapshot of a given pool every 4 hours or so... 
* that script should also dump the snapshot to a temporary location on the machine using ZFS send.
* that file should be checked, compressed, broken up into little bits and checked again... checking is important!
* take those little bits and send them to the datacenter, which will do lots more checking and import the files into the ZFS pool over there...
* there may even be a two way system to send from the datacenter back to the house... 
* finally, the remote pool should be dumped to an SFTP backup system that Hetzner give me... Currently set at 100Gb, but can be increesed as needed...

Thats the "plan"... Lets see how it actually works out... 

Anyway, parts of the process i need to tweak:

* uploading and using as much of my upload bandwidth as possible (2x10mb upload connections...) if i am backing up 800Gb, which should be my first backup, i would like to use both pipes to the fullest... on a single connection, at 50% capacity, it would take 15.1 days to upload. if i can get both connections to work at 80% capacity, giving me 16Mbits/s, it would be down to 4.7 days. With compression and Deduplication, i can probably bring that down a bit more... 
* backing up to SFTP... Reading different things is telling me this might not be such a good idea... 

Some links which you might find useful: 

* [Nexenta][2]: I am using their [Community Edition][7] product for the system.
* [Create a Nexenta Store device in ESXi][3]
* [Configure passthough VMDirectPath in VMWare ESXi][4]: ideally, you should let Nexenta manage your disks... Dont think i can do it wiht the dedicated server, but might be possible with the server in house...

[1]:http://www.hetzner.de/en
[2]:http://nexenta.com/corp/
[3]:http://www.servethehome.com/create-nexentastor-vmware-esxi-virtual-machine/
[4]:http://www.servethehome.com/configure-passthrough-vmdirectpath-vmware-esxi-raid-hba-usb-drive/
[5]:http://en.wikipedia.org/wiki/ZFS
[6]:http://en.wikipedia.org/wiki/ISCSI
[7]:http://www.nexentastor.org/projects/1/wiki/CommunityEdition