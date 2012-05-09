---
layout: post
title: Rekindled Love
---

## Rekindled Love

I've spent the last couple of days rekindling my love for Gentoo, by giving my laptop a fresh start and swanky new installation. This process took about 12 hours in total. That includes configuring X and [Openbox](http://openbox.org/) to a respectable standard, although as it goes with my VM habits I'm sure I'll be making modifications, justifications, and perhaps some stupidfications.

You know, though.. People say modifying and building your Kernel is one of the hardest or at least most laborious tasks involved when configuring a new Linux installation. I disagree. The first time may seem a little daunting, but it's pretty easy to grasp and after a couple of times it's just second nature. One thing which IS a huge annoyance is configuring X. It literally made me burst into a sweat. The thing with X is, even if you know exactly what you're doing, and you've done it 100 times before. This time always seems to be unique.

Luckily I managed to get a tight grip on X, spent a little time configuring my Synaptics touchpad because the default policy frankly sucks, and there I was. Staring at a beautiful new Openbox WM (Honestly, I can't find one I like better, or at least one which is so bloat free and easy to extend and configure, even if it is XML). I'll post a few screenshots of it some time later this week (when I rebuild with a png/jpeg USE flag enabled, whoops).

Then on to setting up my portage overlay! What's this, you non Gentoo users ask? It's [this](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=3&chap=5). Gentoo has a great user guide for Overlays [here](http://www.gentoo.org/proj/en/overlays/userguide.xml). In a nutshell, setting up a portage overlay allows you to inform portage of [ebuilds](http://en.wikipedia.org/wiki/Ebuild) which may not be available in the official portage tree. A great example of this is the [RVM](http://rvm.beginrescueend.com/) ebuild maintained by [Pistos](http://purepistos.net/) and the RVM team. Those ebuilds are available to check out [here](http://github.com/wayneeseguin/rvm/tree/master/pkg/gentoo).

The actual process of compiling didn't take as long as I originally expected, and the Gentoo configuration was as easy and straight forward as I remember the last time I did it. Luckily the famous [Gentoo Handbook](http://www.gentoo.org/doc/en/handbook/) is there to help people every step of the way, if need be. Once I had finished compiling and configuring `git`, `apache2`, `php`, `perl`, `ruby`, `postgresql`, and `mysql`, amongst a few other packages and a ton of Ruby gems. I was back in the game and ready for development. Not losing as much time as I had originally planned. I even managed to sneak in a few games of [Halo](http://www.bungie.net/Stats/Halo3/Default.aspx?player=fyres7orm&sg=0). Huzzah!

Oh and if anyone has any ideas for conquering insomnia, please let me know. I haven't managed to sleep much at all over the past two weeks, any hints or remedies are much appreciated. I'm pretty much at the stage of trying anything, no matter how absurd.
