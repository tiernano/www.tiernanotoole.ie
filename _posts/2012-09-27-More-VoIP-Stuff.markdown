---
layout: post
title: More VoIP Stuff
tags:
- VoIP
---
As part of my ongoing plan to upgrade the house to VoIP, and as a follow up to my first [VoIP stuff][1] post, here are some more things i have found...

* I have added [SipDiscount][2] and [SipGate][3] for making and recieving calls. 
* SipDiscount allows me to set pretty much any number as my Caller ID, as long as i "own" that number (they either text or call you with a code, and you enter it on their site). They also allow me to make cheap calls to Irish Mobiles (check their [rates here][4]) 
* SipGate gave me a incoming UK phone number. Its an 0845 number, which I dont know what that means... but it was free, so its all good. Not sure if i can recieve text messages on it though... 
* I have a [Blueface][5] account, which gives me an Irish 076 VoIP number. 076 is the standard VoIP number here in Ireland... 
* I have a [IpKall][6] number, which is based in Washington State. You need to recieve a call on this line at least once every 30 days to keep it active. 
* My [Google Voice][7] accepts calls and forwards them to my IpKall number, which then rings my BlueFace SIP account (since i know they will be up all the time, by my home server may be offline since i am only testing) which, if a SIP device is connected, will forward it again... if i am offline, or no sip devices are active, that call is redirected to voice mail...

Its all very complicated at the moment, but the plan will be that any incoming calls should go directly to the machine in house, which will ring the desk phone and any other SIP clients. Any incoming PSTN calls will also do the same. Outgoing calls will depend on the dialing plan, which i still need to figure out, but the theory goes as follows:

* Irish landline calls at certin times should go though the PSTN (since we get some free calls with our line). Other times they should go though SipDiscount or BlueFace.
* if the PSTN is busy, fall over to one of the other providers...
* Irish Mobile calls should go though SipDiscount and then fall back to land line, or if i ever get the BlueTooth setup working, SipDiscount, then bluetooth, then landline...
* International calls should be sent though SipDiscount or Blueface, whichever is cheaper...

Its going to be an interesting setup... :)

[1]:http://tiernanotoole.ie/2012/09/11/VOIP-Stuff.html
[2]:http://www.sipdiscount.com
[3]:http://www.sipgate.co.uk
[4]:http://www.sipdiscount.com/rates
[5]:http://www.blueface.ie
[6]:http://www.ipkall.com/
[7]:http://voice.google.com/