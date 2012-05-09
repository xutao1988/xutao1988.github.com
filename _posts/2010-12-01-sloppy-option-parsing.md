---
layout: post
title: Sloppy option parsing
---

## Sloppy option parsing

It's not what you think! I've built [Slop](https://github.com/injekt/slop) to make Option parsing and gathering a lot easier. It's an extremely simple API but incredibly handy for gathering a hash of options out of a string or array. Let's see an example..

{% highlight ruby %}
#!/usr/bin/env ruby

require 'slop'

o = Slop.parse(ARGV) do
  option(:n, :name, "Your name", true) # -n or --name with a required argument
  option(:c, :country, "Your country of residence", :optional => true) # with an optional argument
  option(:a, :age, "Your age", true, :as => Integer) # autoawesome casting
end

# Now we can access the set of options as a Hash (using -n Lee -a 103)
o[:name] #=> 'Lee'
o[:age] #=> 103
o[:country] #=> nil
{% endhighlight %}

You can also omit the `o` assignment and use `Slop.options` to access the last set of options parsed. `Slop.parse()` is just sugar for `Slop.new().parse()` so you can predefine your options and rules before you start throwing strings and arrays into `parse()`.

Now you're probably thinking "*What's wrong OptionParser in stdlib??*" Well, nothing. I really like OptionParser. I just find myself writing code like this a lot:

{% highlight ruby %}
require 'optparse'

options = {}

opt = OptionParser.new do |opt|
  opt.on("-n", "--name NAME", "Your name") do |n|
    options[:name] = n
  end

  opt.on("-a", "--age AGE", "Your age") do |a|
    options[:age] = a
  end

  opt.on("-c", "--country [COUNTRY]", "Your country of residence") do |c|
    options[:country] = c
  end
end

opt.parse(ARGV)
{% endhighlight %}

Which is fine, but it seems like a lot when the above code in Slop is essentially doing exactly the same thing, without all of the blocks.

Slop is still extremely pre production, hence the `v0.1.4` tag. But it's waiting for issues and feedback! Be sure to check out the [README](https://github.com/injekt/slop#readme) for more information.