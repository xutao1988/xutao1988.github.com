---
layout: post
title: Don't be scared of a little Gem
---

## Don't be scared of a little Gem

So I had a conversation with a guy on IRC the other day regarding a task he wanted to achieve using Ruby. Without boring you with the details, here's how it went:

{% highlight text %}
matt> Hi I'm looking for help with a script. I'm attempting to send multiple HTTP requests in a single
           session whilst collecting and securing cookie information, session based too.
injekt> matt: Check out the Mechanize library: http://mechanize.rubyforge.org/mechanize/
matt> injekt: what is that?
injekt> matt: Read it and find out? :)
matt> injekt: I don't want to install a gem for this
injekt> matt: Why not? All the hard work is done for you
matt> because it's more libraries the user has to install, i want to write it myself
injekt> matt: If the user is using your library aren't they already using a gem?
matt> no
injekt> matt: How so?
matt> im not using gems
injekt> matt: Why not?
matt> I dont want to install gems, it means more for user to do
matt> forget it jesus christ everyone keeps telling me to use rubygems
* matt has quit (Quit: dumb shit)
{% endhighlight %}

Well matt, there is a reason for that. This day in age people need to be less scared of using package managers and contributed libraries. Try it, if it sucks, try another one. Once you've exhausted all possibilities and you're still not happy, then build it yourself. Once you've done that, release it and tell people why it's better than the others. It's a process still so many people are benighted to. A process so simple I could explain it to my Nan over tea and biscuits.

The same has been said many times before in the Perl community (one I used to inhabit). Countless times on Dev Shed has someone asked how to parse some ill formatted markup, only to be told they should be using a library like HTML::TokeParser, and rightfully so. What's wrong with using third party libraries and relying on a packaging system like CPan or RubyGems?

Nothing. That's what.