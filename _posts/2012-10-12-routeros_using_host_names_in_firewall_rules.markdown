---
layout: post
tags:
- RouterOS
- Firewall
- Networking
title: RouterOS Using Host names in Firewall Rules
date: 2012-10-12  7:43:17
---
As a follow up to yesterday's post on [RouterOS Blocking Machine access to all but one IP][1] I tought i would show how to add extra IPs to that list, without having a shedload of firewall filters.

* First things first, get your list of IPs you allow access to. In my case, i just did an NSLOOKUP on the name and got the IPs.
* Create an "Address List" in RouterOS. This can be done on the Web Interface by going to IP / Firewall / Address List and clicking Add. I had none previously, so i created a new rule, naming it [ExpressVPN][2] (the lads i use for VPN access) and added the first address.
* this is where things get interesting. for extra IP (for ExpressVPN, i have 4) you create a new address with the SAME name, but different IP.
* in your firewall rule, you should have either a src address or dst address. in my case, i had both, but this was a change for the dst address. I removed the address from the rule, i added it as a dst address list entry. If you have multiple address lists, you will see them here.

to do this at the command prompt:

{% gist 3877692 %}

this will block any traffic, other than the IPs in the expressVPN address list, for the machine 192.168.0.123.

[1]:http://tiernanotoole.ie/2012/10/11/routeros_blocking_machine_access.html
[2]:www.expressvpn.com/?referrer_email=tiernan@tiernanotoole.ie/
