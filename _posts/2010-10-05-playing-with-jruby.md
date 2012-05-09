---
layout: post
title: Playing with JRuby
---

## Playing with JRuby

Over the last couple of days, many Ruby-ist Twitter followers will have noticed the flourishing overgrowth of tweets directed at and around the [JRubyConf](http://jrubyconf.com/). Being a huge fan of both Java and Ruby, I was watching with boundless engrossment. Unfortunately I haven't yet seen any of the slides/videos from the speakers but I'm hoping some come along soon.

I've taken this time to dive into [JRuby](http://jruby.org/) a little more. And what's the outcome? mind == blown. Whilst I never really take the time out to truly indulge myself in a language enough to build extensions or read through the generally boggling platform source code, I took a shine to JRuby. I've been shunned back into some Java code this week (Don't worry, that's a good thing) and I've enjoyed it (no, **seriously**). JRuby is the tip of the iceberg.

Here, let's see a quick example of using the [Standard Widget Toolkit](http://www.eclipse.org/swt/) to extend a JRuby script and implement a simple GUI example.

{% highlight ruby %}
require 'java'
require '~/downloads/swt/swt'

module SWT
  import org.eclipse.swt.widgets.Display
  import org.eclipse.swt.widgets.Shell
end

class GUI
  include SWT

  def initialize(title)
    @display = Display.new
    @shell = Shell.new(@display)
    @shell.set_text(title)
    @shell.set_size(500, 300)
  end

  def run!
    @shell.open

    while not @shell.is_disposed
      if not @display.read_and_dispatch
        @display.sleep
      end
    end
  end

end

GUI.new("Howdy").run!
{% endhighlight %}


The second line is fetching the `swt.jar` file from the downloads directory and with JRubys magical `java` include, we have our hands on the `import` method, which is grabbing the Java classes and throwing them into a Ruby module. Right about now your brain is probably exploding, but it's ok, you'll get used to it.

Check out the [calling Java from Ruby](http://kenai.com/projects/jruby/pages/CallingJavaFromJRuby) wiki article for some more awesome extras that will no doubt entertain you. I'm off to play with SWT and JRuby a little more! I'll try and post something later this week with more information.


