---
layout: post
title: RVM plays nice on production
---

## RVM plays nice on production

Some of you may have read my earlier entry regarding RVM entitled Where for art thou RVM (those of you who have not should go read it now before anything drastic happens, such as my website punching you in the face for not doing so). Only kidding, my website loves you!

Anyway, I was speaking to some guys the other day regarding RVM and its super duper serious awesomeness and stuff. Here's basically how the conversation went:

{% highlight text %}
injekt> Woop rvm ftw!
dave> Yeah rvm is awesome
alan> agreed
alan> love it for development. What do you guys use for production servers though?
dave> I have ruby 1.9.1 here
injekt> ... rvm
alan> huh?
injekt> Why don't you use rvm for production? I do
alan> isn't it for development
injekt> it's for managing multiple Ruby installs + much more
injekt> Who said it was just for development?
injekt> I use it for production on 3 servers, 2 of which are public shell servers
alan> Oh, I thought...
injekt> YOU THOUGHT WRONG
injekt> RVM SHALL DISMISS YOUR EXISTENCE AND CURSE YOU WITH TERRIBLE RUBIES
alan> ugh..
{% endhighlight %}

Yeah, I got a little excited at the end. I apologise for that.

**NOTE** Before continuing please note that the regular installation script found
[here](http://rvm.beginrescueend.com/rvm/install/) will work as expected when ran as the
root user. This will install RVM and create shared access across all users.

When I first started playing with RVM I wanted to come up with a way of allowing users to share rubies and install system wide gems, allowing them to have a free and open development environment which in turn increasingly nudges their dev habitat up the awesome scale. Win win.

The setup I have basically mimics that of the one found [here](http://greg.nokes.name/2010/03/26/rooting-with-rvm/), an awesome post for users who want to install RVM as the root user. These are basically the steps I took (and continue to take) on my development servers:

1. Switch to root user: `su root`
2. Grab the latest RVM code from github: `git clone git://github.com/wayneeseguin/rvm.git`
3. `cd rvm`
4. `./install`
5. Watch the pleasures of RVM christening your system with its awesome juicy curvaceous..ness
6. Remove the rvm folder: `rm -rf rvm`
7. Add rvm group: `groupadd rvm`
8. Add yourself to said group: `usermod -aG rvm injekt`
9. Add `rvm_path` to `/etc/rvmrc`: `echo "export rvm_path=/usr/local/rvm" > /etc/rvmrc`
10. Open up `/etc/profile` and add [these](https://gist.github.com/886070) lines
11. Give the rvm group ownership to it's rightful rubies: `chown -R root:rvm /usr/local/rvm`
12. Give write access to all members of the rvm group: `chmod -R g+w /usr/local/rvm`
13. Switch back to non-root: `exit`
14. Dance a little bit
15. `rvm install <ruby version>`
16. Eat sammich
17. Set default Ruby version: `rvm use <ruby version> --default`
18. Profit

Before you ask; yes this does mean all users of the `rvm` group have access to rubies and gems. This isn't meant to tell you the best method of configuring rvm for cross user server use, but rather the method I use.

Official installation notes are [here](http://rvm.beginrescueend.com/rvm/install)