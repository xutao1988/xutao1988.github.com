---
layout: post
title: Hello, World!
---

## Hello, World!

Howdy. Welcome to my third attempt at creating a blog. I've been using [Wordpress](http://wordpress.org/) for some time now, and I've decided it's time to move on.

Don't get me wrong, Wordpress is a great and powerful blog management system. It's just... too much. Wordpress offers too many options, too much functionality. I'd rarely use even half of it. Wordpress is like Daphne, she's hot and offers everything you could want, but sometimes I just need to stick with Scooby. He's always been there for me, and he's simple, not complicated like Daphne.

This blog is powered by the high quality Ruby libraries [Sinatra](http://sinatrarb.com/), [Sequel](http://sequel.rubyforge.org/) and [RDiscount](http://github.com/rtomayko/rdiscount). Now I know what some of you are thinking; wait, you're using Sinatra?! What happened to [Ramaze](http://ramaze.net)? Well, nothing. I love Ramaze, I just wanted to try Sinatra for this. You don't hate me, do you?

Here's the ditty:

1. Sinatra throws up a pretty hot XHTML page for your viewing pleasure
2. You request an entry
3. Sinatra throws the ball to Sequel
4. Sequel does some tricks, querying the database and such ([PostgreSQL](http://www.postgresql.org/))
Sequel asks RDiscount for some markdown
5. RDiscount is all *yeah, sure bro!*, and cooks up a markdown sammich
6. Sequel passes the yummy lunch time snack back to Sinatra
7. Sinatra uses [HAML](http://haml-lang.com/) to ensure prettiness of markdown
8. Ka boom

Pretty neat, huh?

If you'd like to see what the original markdown looks like before RDiscount works its magic, just throw on a .txt extension to the end of an entry url. Something like [this](http://blog.injekt.net/1/hello-world.txt).

On that note,
Props to Scooby