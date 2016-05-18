---
layout: computers
title: GodBox v2
sitemap:
    priority: 0.7
    changefreq: 'weekly'
    lastmod: 2016-05-18T13:30:00
---

# GodBox V2

Dell [Precision T7600 Workstation][9]:

* Dual 8 Core Xeons ([E5-4620][2] @ 2.2Gz each)
* 96Gb RAM (DDR3)
* 2 256Gb [Samsung 850 Pro][3] SSDs (RAID 0 from the PERC Controller onboard)
* Storage setup in Windows Storage Spaces (4x 2Tbs with a 256GB and 128GB SSD in a single pool) split into a 2TB Mirrored disk (with SSD tiering) for important VMs and a 2TB striped disk (also with SSD tiering) for not so important VMs...
* [Drobo 5D][1] with 2X4Tb drives and 2X2Tb and a 1Tb drive (13Tb RAW, ~10Tb usable)
* NVidia [Geforce GTX 970][4] graphics card
* 1 Dell 2007WFP Monitors and 2 [Dell P2815Q][5] (4k) Monitors
* Currently running Windows Server 2012 R2 with Hyper-V

![godboxv2-CPU details](/post_images/2016/03/29/20160329-godboxv2-cpu.png)


[1]: http://www.amazon.co.uk/gp/product/B008S02S54/ref=as_li_tl?ie=UTF8&camp=1634&creative=19450&creativeASIN=B008S02S54&linkCode=as2&tag=tiescomclo-21&linkId=S3TRJOV2MB4ZOGJK
[2]: http://ark.intel.com/products/64607/Intel-Xeon-Processor-E5-4620-16M-Cache-2_20-GHz-7_20-GTs-Intel-QPI
[3]: http://www.amazon.co.uk/gp/product/B00LMXBOP4/ref=as_li_tl?ie=UTF8&camp=1634&creative=19450&creativeASIN=B00LMXBOP4&linkCode=as2&tag=tiescomclo-21&linkId=ZZLV7VDTOMJOLNCK
[4]: http://www.amazon.co.uk/s/?_encoding=UTF8&camp=1634&creative=19450&field-keywords=Geforce%20GTX%20970&linkCode=ur2&tag=tiescomclo-21&url=search-alias%3Daps&linkId=4FFJX5JH2LEGISJ4
[5]: http://www.amazon.co.uk/gp/product/B00IOUBOB2/ref=as_li_tl?ie=UTF8&camp=1634&creative=19450&creativeASIN=B00IOUBOB2&linkCode=as2&tag=tiescomclo-21&linkId=736XUUGW2KINESGB
[6]: https://btrfs.wiki.kernel.org/index.php/Main_Page
[7]: http://www.sabayon.org
[8]: http://www.vmware.com/products/workstation
[9]: http://www.dell.com/ie/business/p/precision-t7600/pd
