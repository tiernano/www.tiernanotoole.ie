---
layout: post
tags:
- Storage
- Backup
- Code
title: Hubic and Duplicity
date: 2015-04-01 07:00:00
---

I mentioned [HubiC][1] in my [last post][3], and in it i said that you could use [Duplicity][4] for backups. Well, this is how you get it to work...

First, i am using Ubuntu 14.04 (i think...). I use [Ubuntu][9] in house for a few things:

* its running [Tiernan's Comms Closet][5], [GeekPhotographer][6] and [Tiernan's Podcast][7] all in house, aswell as being used to [build this site][8]. The Web Server and MySQL Server are seperated, MySQL running on Windows, web on Ubuntu... but thats a different story...
* I have a couple of proxy servers running Ubuntu also
* Other general servers running Ubuntu... dont ask, cause i cant remember what they do half the time...

So, [Duplicity][4] is a backup application. From their website:

What is it?

Duplicity backs directories by producing encrypted tar-format volumes and uploading them to a remote or local file server. Because duplicity uses librsync, the incremental archives are space efficient and only record the parts of files that have changed since the last backup. Because duplicity uses GnuPG to encrypt and/or sign these archives, they will be safe from spying and/or modification by the server.

The duplicity package also includes the rdiffdir utility. Rdiffdir is an extension of librsync's rdiff to directories---it can be used to produce signatures and deltas of directories as well as regular files. These signatures and deltas are in GNU tar format.

So, how do we get it working? Well, givin that i am on Ubuntu, these are the steps i needed to do:

* first, we need some credentials and API keys... If you havent signed up for [HubiC][1] Do so now... That url gets you an extra 5Gb if you sign up for free (usually 25Gb) or if you pay 1EUR a month, you get 110Gb (usually 100Gb) and 5EUR a month gets you a staggering 10TB (yup! Terabytes!).
* Login to Hubic, and in the menu go to 'My Account', 'Developers'. in here, create a new application (name and URL to redirect to... http://localhost seems to work correctly). Get the Client ID and Secret ID that was given to you.
* take the contents of [the following gist][10] and replace your own details... I know, i am not a fan of sticking my password in a txt file... but it should be your local machine...
* that file should be in your home directory and should be called .hubic_credentials.
* add the duplicity PPA project ([https://launchpad.net/~duplicity-team/+archive/ubuntu/ppa][2]) to ubuntu using the add-apt-repository command (details on the link above, under the link 'read about installing'). for me, i just called 'sudo add-apt-repository ppa:duplicity-team/ppa'
* install duplicity by doing 'sudo apt-get install duplicity'. Dont forget (its in the tutorial above!) to do an 'sudo apt-get update' first!
* When i ran that, there where a few extra Python packages to be installed, so i was asked did i want to install them... Say, yes.
* Now, to run a backup we run the following command:

<pre>duplicity ~/ cf+hubic://location</pre>

* cf+hubic is the backend to use, ~/ is the url to backup (my home directory in this case) and location is where on Hubic we want it stored. If this doesent exist, not a problem... it will create it.
* after we run this we... ahhh... i get an error:
<pre>BackendException: This backend requires the pyrax library available from Rackspace.</pre>
* right... [pyrax library][11] is from Rackspace and is available to download though pip...
* I seem to have python and a few other bits installed on this machine, so running 'sudo pip install pyrax' works... Your millage may vary... [eg, this is out of scope for this tutorial! your on your own!]
* Other problem... I got a load of weird and wondering errors like this:

<pre>AttributeError: 'Module_six_moves_urllib_parse' object has no attribute 'SplitResult'</pre>

* I fixed these by running:

<pre> sudo pip install furl --upgrade</pre>

* FINALLY! ITS ALIVE!!! by default, it asks you for a key for the GnuPG encryption... and its all good! the first backup creates the directories, required files, etc. the next time you run the command, it will only upload changes. it will also ask for your GnuPG code you entered, so remember it!

And thats all folks! Any questions, leave them in the comments!

[1]: https://hubic.com/home/new/?referral=GMSQVQ
[2]: https://launchpad.net/~duplicity-team/+archive/ubuntu/ppa
[3]: https://www.tiernanotoole.ie/2015/03/31/HubiC_SWIFT_CURL.html
[4]: http://duplicity.nongnu.org/
[5]: http://blog.lotas-smartman.net
[6]: http://www.geekphotographer.com
[7]: http://podcast.tiernanotoole.ie
[8]: http://tiernanotoole.ie/2012/08/29/NewSite.html
[9]: http://www.ubuntu.com
[10]: https://gist.github.com/tiernano/86ab2e08ba4e588a343a
[11]: https://github.com/rackspace/pyrax
