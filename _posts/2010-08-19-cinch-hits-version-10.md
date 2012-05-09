---
layout: post
title: Cinch hits version 1.0
---

## Cinch hits version 1.0

That's right, folks. The merge is complete! We (Dominik, more than I) have been hard at work pushing for the 1.0 release. The [Cinch IRC Bot Building Framework](http://doc.injekt.net/cinch) has officially hit version 1.0. Check out the documentation here for more information or view the changes we've made [here](http://github.com/injekt/cinch/commits/master).

This version boasts support for threading and plugins, and we've packed a bunch of examples to get you going! Check out the examples [here](http://github.com/injekt/cinch/tree/master/examples/). Don't forget though guys if you're updating from an existing version of Cinch then you are without doubt going to encounter some backwards incompatible changes. I promise you though that these changes are more than worth your time. You can now convert your block-syntax rules into fully fledged self-contained plugins. How cool is that!

Over the next few days I'll be creating some documentation to help support you guys on making the transition from existing versions of Cinch. Though this should be a trivial task. Just for good measure, let me give you an example of Cinch's Google plugin.

{% highlight ruby %}
require 'cinch'
require 'open-uri'
require 'nokogiri'
require 'cgi'

class Google
  include Cinch::Plugin
  match /google (.+)/

  def search(query)
    url = "http://www.google.com/search?q=#{CGI.escape(query)}"
    res = Nokogiri::HTML(open(url)).at("h3.r")

    title = res.text
    link = res.at('a')[:href]
    desc = res.at("./following::div").children.first.text
  rescue
    "No results found"
  else
    CGI.unescape_html "#{title} - #{desc} (#{link})"
  end

  def execute(m, query)
    m.reply(search(query))
  end
end

bot = Cinch::Bot.new do
  configure do |c|
    c.server = "irc.freenode.net"
    c.nick   = "MrCinch"
    c.channels = ["#cinch-bots"]
    c.plugins.plugins = [Google]
  end
end

bot.start
{% endhighlight %}

Run the code and be prepared for awesome-ness! We'll be making improvements to Cinch throughout, so let us know if you have any features or you find any bugs and report them [here](http://github.com/injekt/cinch/issues). Have fun with the new Cinch!