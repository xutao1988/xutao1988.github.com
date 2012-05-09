---
layout: post
title: Colourful codez
---

## Colourful codez

For those of you who pay any attention to the absurd applesauce I spend countless hours typing into this blog, you may have noticed the design changing yet **again**. Yep the grey annoyed me. I've also started using [Albeano](https://github.com/injekt/albeano) for highlighting code snippets inside of my posts. It's a simple library consisting of a couple of methods but it's an incredibly handy wrapper around [Albino](http://github.com/github/albino) which is in turn a wrapper around [Pygments](http://pygments.org). Pygments is probably one of (if not) the best syntax highlighting libraries around.

Here, it's easy..

{% highlight text %}gem install albeano{% endhighlight %}

{% highlight ruby %}
#!/usr/bin/env ruby

html = Albeano.generate(source_code)
{% endhighlight %}

Yep, it's that simple. You can even return markdown (that's what I'm doing!)

{% highlight ruby %}Albeano.new(source_code).to_markdown{% endhighlight %}

Which requires the [RDiscount](https://github.com/rtomayko/rdiscount) library.

Here's the CSS I'm using to highlight the code:

{% highlight css %}
.highlight {
  font-size: 1.1em;
  color: #000;
  background: #fff;
  padding: 15px;
  border-top: 1px solid #ccc;
  border-bottom: 1px solid #ccc;
  margin: 15px 5px;
}
.highlight .c{color:#998;font-style:italic;}
.highlight .err{color:#a61717;background-color:#e3d2d2;}
.highlight .k{font-weight:bold;}
.highlight .o{font-weight:bold;}
.highlight .cm{color:#998;font-style:italic;}
.highlight .cp{color:#999;font-weight:bold;}
.highlight .c1{color:#998;font-style:italic;}
.highlight .cs{color:#999;font-weight:bold;font-style:italic;}
.highlight .gd{color:#000;background-color:#fdd;}
.highlight .gd .x{color:#000;background-color:#faa;}
.highlight .ge{font-style:italic;}
.highlight .gr{color:#a00;}
.highlight .gh{color:#999;}
.highlight .gi{color:#000;background-color:#dfd;}
.highlight .gi .x{color:#000;background-color:#afa;}
.highlight .go{color:#888;}
.highlight .gp{color:#555;}
.highlight .gs{font-weight:bold;}
.highlight .gu{color:#800080;font-weight:bold;}
.highlight .gt{color:#a00;}
.highlight .kc{font-weight:bold;}
.highlight .kd{font-weight:bold;}
.highlight .kp{font-weight:bold;}
.highlight .kr{font-weight:bold;}
.highlight .kt{color:#458;font-weight:bold;}
.highlight .m{color:#099;}
.highlight .s{color:#d14;}
.highlight .na{color:#008080;}
.highlight .nb{color:#0086B3;}
.highlight .nc{color:#458;font-weight:bold;}
.highlight .no{color:#008080;}
.highlight .ni{color:#800080;}
.highlight .ne{color:#900;font-weight:bold;}
.highlight .nf{color:#900;font-weight:bold;}
.highlight .nn{color:#555;}
.highlight .nt{color:#000080;}
.highlight .nv{color:#008080;}
.highlight .ow{font-weight:bold;}
.highlight .w{color:#bbb;}
.highlight .mf{color:#099;}
.highlight .mh{color:#099;}
.highlight .mi{color:#099;}
.highlight .mo{color:#099;}
.highlight .sb{color:#d14;}
.highlight .sc{color:#d14;}
.highlight .sd{color:#d14;}
.highlight .s2{color:#d14;}
.highlight .se{color:#d14;}
.highlight .sh{color:#d14;}
.highlight .si{color:#d14;}
.highlight .sx{color:#d14;}
.highlight .sr{color:#009926;}
.highlight .s1{color:#d14;}
.highlight .ss{color:#990073;}
.highlight .bp{color:#999;}
.highlight .vc{color:#008080;}
.highlight .vg{color:#008080;}
.highlight .vi{color:#008080;}
.highlight .il{color:#099;}
{% endhighlight %}

A lot of the span styles are copied from GitHubs [Gist](http://gist.github.com) tool, because I really like them, so all credit to those guys.

In other news, there's been a few discussions regarding Refinements in Ruby 2.0. I recommending reading both [this blog post](http://timeless.judofyr.net/refinements-in-ruby) by Magnus Holm and [this one](http://yehudakatz.com/2010/11/30/ruby-2-0-refinements-in-practice/) from Yehuda Katz. Interesting stuff!