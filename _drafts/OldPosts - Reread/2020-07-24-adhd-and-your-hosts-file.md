---
layout: post
title: ADHD and Your HOSTS file
date: 2020-07-24 07:53
author: k3ntuckyblog
comments: true
categories: [ADHD, ADHD Systems, Blocking websites, Computers, Customizing, Distracted Web Surfing, HOSTS file, Security]
---

<<<<<<< HEAD
-OR- Let's learn how to block websites with the HOSTS file.
=======
**-OR- Let's learn how to block websites with the HOSTS file.**
>>>>>>> 0cdcb504a4e1ea52f45c7d8817156703e9886e36

We all like the internet, right?  Well, 'Like' is a strong word for like 98% websites.  Porn, gambling, social media and generally distracting websites are all well and good until you get to the point where 'like' get replaced with 'get sidetracked by'.  For people with ADHD, the internet can easily become a major distraction.  

Between algorithms finding one more article you'd probably like to read, video playlists that can easily railroad your attention or going down a Wikipedia article hole.  You start reading about Northern Kentucky University next you know you're reading about Belgian long-distance runner, Els Rens.  Oh wow, she placed 84th in the marathon at the 2016 Olympics.  That's way better then I would do.  I should finally start that couch to 5k program. Next thing you know, you're half way around the block and think "Wait, oh crap, I was writing...".  One click can easily result in a few hours of distracted, mindless, unproductive surfing.

Joy-surfing isn't always bad, all things in moderation, right?  But it's easy to make a short break into a half day internet excursion trying to find that one thing from that one time and then having to rush to finish what you were trying to do.  The character Oma Desala from Stargate SG-1 has a great line, "The temptation of my subconscious is too great, So I deny it battle." My HOSTS file has denied a number of those battles.

I also want to add real quick, You can also block ad networks and known malicious domains with this method as well.  It adds an additional layer to your security posture and protects your information a little bit more.  This isn't an end all method, but it comes in handy. 

Before we go on, let me assure you, this is a quick overview of how to edit the hosts file on Windows computers.  This wouldn't be a full blown explanation about how DNS works (Basically DNS translates human readable word addresses (Google.com) computer readable to numerical IP addresses (217.160.0.201). There you go, insultingly short and sweet).  This is here to give you enough information to be able to add / remove sites yourself.

<<<<<<< HEAD
Before we execute, let's take some time and make a backup of the HOSTS file.  Go to ##C:\Windows\System32\drivers\etc\## and right click on HOSTS (HOSTS doesn't have an extension, but you can open it with notepad) > Select copy > then right click an empty part of the file explorer window > select paste.  There we go, you can right click the newly created file and rename to HOSTS.old or HOSTS.backup if you want. Please note, The HOSTS file is important to your system.  Interestingly enough, Your HOSTS file is basically empty.  Everything inside is commented out, meaning nothing gets processed.  Normally you don't have to worry about the HOSTS file unless your computer is acting as a server.

All right, let's execute this plan.  To begin, You can't just edit the HOSTS file as a regular user.  You'll want to go to the start menu > search for 'notepad' > right click it and select 'run as administrator'.  If you're not an admin on your computer you'll need to find out who is.  Once you have notepad running as administrator, open up ##C:\Windows\System32\drivers\etc\hosts## .
=======
Before we execute, let's take some time and make a backup of the HOSTS file.  Go to **C:\Windows\System32\drivers\etc\**and right click on HOSTS (HOSTS doesn't have an extension, but you can open it with notepad) > Select copy > then right click an empty part of the file explorer window > select paste.  There we go, you can right click the newly created file and rename to HOSTS.old or HOSTS.backup if you want. Please note, The HOSTS file is important to your system.  Interestingly enough, Your HOSTS file is basically empty.  Everything inside is commented out, meaning nothing gets processed.  Normally you don't have to worry about the HOSTS file unless your computer is acting as a server.

All right, let's execute this plan.  To begin, You can't just edit the HOSTS file as a regular user.  You'll want to go to the start menu > search for 'notepad' > right click it and select 'run as administrator'.  If you're not an admin on your computer you'll need to find out who is.  Once you have notepad running as administrator, open up **C:\Windows\System32\drivers\etc\hosts**.
>>>>>>> 0cdcb504a4e1ea52f45c7d8817156703e9886e36

OK, let's block a site...  Where's a site?  I just had one... Oh, here we go!

Inside notepad we're going to put '0.0.0.0 pornhub.com' and hit save...
<<<<<<< HEAD

## WAIT, COME BACK! ## We can fix it later (Sometimes you won't be able to save because your computer is consulting the HOSTS file.  Wait a few minutes and try again). ##
=======
>>>>>>> 0cdcb504a4e1ea52f45c7d8817156703e9886e36

**WAIT, COME BACK!** We can fix it later (Sometimes you won't be able to save because your computer is consulting the HOSTS file.  Wait a few minutes and try again).

All right, so...  Once we have the entry in; open up your web browser(s) (If you have more then one, open them as well.  Because it's on the system level, it works no matter the browser.), don't tell your parents I said this, but make sure the coast is clear and try going to pornhub.com.  You should get a pornhub.com cannot be reached / page hasn't responded error.  If you still get the page (OOH! busted! You dirty!), close your browser (QUICK!) and reopen.  More then likely you have the IP stored in a cache.

Let's break down what we wrote and what happens:  When you try going to a website, your computer will need to translate 'pornhub.com' to something it can use.  It searches the HOSTS file to see if it can find an IP address.  If there's no entry for the website, your computer will send out requests to DNS servers to try and figure out the IP address.  Because we have an entry in the HOSTS file for pornhub.com assigned to 0.0.0.0 it will use that address.  The numerical address '0.0.0.0' doesn't have a page, so the browser assumes the host isn't reachable.  This is how we deny battle to the temptation of mindless surfing.

Note: Sometimes adding '0.0.0.0 website.com' doesn't block the web page because the actual site is at www.website.com. I add both to the HOSTS file to cover my bases.

*But K3ntucky, do you know how many websites there are? Hundreds, literally hundreds! How can I block them all?*

<<<<<<< HEAD
A lot of smart people on the internet have taken the time to curate HOSTS lists for others to use.  I personally like the list made by a gentleman named ["https://github.com/StevenBlack/hosts"](Steven Black).  He creates huge HOSTS files, ranging from 57,294 to 82,879 unique domains, and splits them into 15 variations to focus on your particular need.  Find a curated list of sites, add them to your HOSTS files and then add your specific sites disruptive to your productivity and you've created a system to protect yourself.  You've denied the battle and by default won.  It's not perfect, as you can always go in and unblock it.  But it's a way forward.

Now that we know how to edit the HOSTS file manually, I can let you in on a program I found.  Another gentleman named ["https://github.com/scottlerch/HostsFileEditor"](Scott Lerch) created a program that makes editing the HOSTS file really easy.  It's called Hosts File Editor and it's hosted on his github page.

## What the heck, K3ntucky, you made me read all that mess before you talking about the program that handles all that nerd crap? ##
=======
A lot of smart people on the internet have taken the time to curate HOSTS lists for others to use.  I personally like the list made by a gentleman named ["https://github.com/StevenBlack/hosts ]Steven Black.</a>  He creates huge HOSTS files, ranging from 57,294 to 82,879 unique domains, and splits them into 15 variations to focus on your particular need.  Find a curated list of sites, add them to your HOSTS files and then add your specific sites disruptive to your productivity and you've created a system to protect yourself.  You've denied the battle and by default won.  It's not perfect, as you can always go in and unblock it.  But it's a way forward.

Now that we know how to edit the HOSTS file manually, I can let you in on a program I found.  Another gentleman named ["https://github.com/scottlerch/HostsFileEditor ]Scott Lerch</a> created a program that makes editing the HOSTS file really easy.  It's called Hosts File Editor and it's hosted on his github page. 

*What the heck, K3ntucky, you made me read all that mess before you talking about the program that handles all that nerd crap?*
>>>>>>> 0cdcb504a4e1ea52f45c7d8817156703e9886e36

Yeah, I did.  I find it's better to learn the long way then learn the shortcuts.  Some people like having the manual method, some people like using the program.  Either method is good so long as you use it and maintain your file.  

Be warned - If you make your HOSTS file too big (so far I've noticed too many entries is around 85,000) your general website surfing will start off slow, but eventually get better.

TL;DR
<<<<<<< HEAD

If distracted websurfing is too much of a temptation, deny it battle by blocking the website at the computer level by adding it to your HOSTS file.

You can also use your HOSTS file to block known ad networks and malicious domains to add an extra layer to your computer security posture.

For Windows, run notepad as administrator and open ## C:\Windows\System32\drivers\etc\hosts ## and put '0.0.0.0 website.com' and '0.0.0.0 www.website.com'.

["https://github.com/StevenBlack/hosts"](Steven Black) curates HOSTS lists and splits them into 15 groups so you can find one for your specific propose.

["https://github.com/scottlerch/HostsFileEditor"](Scott Lerch's Hosts File Editor) program makes editing the HOSTS file easy.

=======
>If distracted websurfing is too much of a temptation, deny it battle by blocking the website at the computer level by adding it to your HOSTS file.
>You can also use your HOSTS file to block known ad networks and malicious domains to add an extra layer to your computer security posture.
>For Windows, run notepad as administrator and open `C:\Windows\System32\drivers\etc\hosts` and put '0.0.0.0 website.com' and '0.0.0.0 www.website.com'.
>["https://github.com/StevenBlack/hosts ]Steven Black</a> curates HOSTS lists and splits them into 15 groups so you can find one for your specific propose.
>["https://github.com/scottlerch/HostsFileEditor ]Scott Lerch's Hosts File Editor</a> program makes editing the HOSTS file easy.
>>>>>>> 0cdcb504a4e1ea52f45c7d8817156703e9886e36
