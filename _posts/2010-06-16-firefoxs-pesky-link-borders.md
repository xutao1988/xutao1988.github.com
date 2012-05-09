---
layout: post
title: Firefox's pesky link borders!
---

## Firefox's pesky link borders!

If you're a [Firefox](http://mozilla.com/firefox/) user you may find from time to time that when visiting a website and carrying out the rather intelligible task of focusing on an image link, you're confronted with a rather obtuse border. Now from a web developers point of view, this matters.

You may not have noticed this mystifying feature before, but it's there, I promise. You can in fact go ahead and see for yourself at popular websites such as Google and Amazon (of course if you are not a Firefox user please do not send me complaint letters because you cannot see this border). Here's an example..

Wanna fix it?

Try adding the following to your CSS:

{% highlight css %}a { outline: none }{% endhighlight %}

or if you want to be fancy and direct:

{% highlight css %}a:focus { outline: none }{% endhighlight %}

This will remove all outlines on your focused image links. Neat, right?