---
layout: post
tags:
- Networking
- PFSense
- Hardware
- HomeLab
title: Network and HomeLab V.Next (Part 3)
date: 2015-07-16 13:15:00
---
So, this part of my article set will be talking specifically about the router and wireless network. At the moment, my router is way overkill:

* Old HP Proliant ML110 G5
* [Intel Core2Quad Q6600][1]
* 8 Gb RAM
* total of 12 Gigabit network cards (of which 4 are currently used...)
* 500Gb HDD

I have been playing with some networking in the house and have managed to build some VLANs. The modems are connected both directly to the Router
and to a dedicated switch port for a given VLAN. The plan for the upgrade, which i hope to complete sooner than the rest of the network is as
follows:

* get the ML110 running [ESXi][3] and visualize [PFSense][2]. Give it 2gb of RAM and some processor.
* take some of the network cards out of the box. It does not need 12 ports, but maybe leave the 2 quad ports in there. They should be connected
to the main switch trunked. 8 may be overkill, but i never do things by half.
* the PFSEnse VM should be connected to all 3 WAN VlANs (900, 901 and 902) and should also have at least one port to the LAN. There may also be
other ports for other internal VLANs.

with the spare processor, i can then add other (small) VMs to this machine.


[1]:http://ark.intel.com/products/29765/Intel-Core2-Quad-Processor-Q6600-8M-Cache-2_40-GHz-1066-MHz-FSB?q=Q6600
[2]:http://www.pfsense.org
[3]:https://www.vmware.com/products/vsphere-hypervisor
