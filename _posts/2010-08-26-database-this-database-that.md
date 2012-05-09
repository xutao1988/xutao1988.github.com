---
layout: post
title: Database this, Database that
---

## Database this, Database that

After taking the time to configure and in-sculpt my new Gentoo installation, I thought I'd have a little play with MySQL and PostgreSQL. I've had a self confined debate about which database engine I should use. I use MySQL a lot for client work, and it's quite a standard amongst mainstream PHP development, a sector I unfortunately inhabit.

So why am I even thinking of using PostgreSQL? Why don't I just shut up and stick with MySQL? Well..

Back in the old days (ie a few years ago, for me). There wasn't a choice. At least not in the environment I was working in. MySQL was etched into the walls of the bathroom, it had left burn marks on the hands of the debilitated developers. The inadequate, harrowing error messages became a poetic nuisance easily dealt with and sometimes even foreseen.

Isn't that terrible? It sure is. Then again so is getting up at 5am, but you just get used to it once you've done it for a while.

I'm not one of these programmers who bitches about writing raw SQL statements. I've read many quotes which publicly refute any charm this language contains. Personally for me, writing raw SQL is secluded bliss. I won't lie I do like my ORMs when I'm using Ruby, namely [Sequel](http://sequel.rubyforge.org/), but I don't use the likes of phpMyAdmin and similar tools. Writing SQL is natural if not a little mundane at times. It's something I believe every developer should encounter and it's worth time learning.

OK so now you're wondering where I'm going with this, you're all "Look, bro.. you started talking about MySQL and PostgreSQL and haven't mentioned why you'd use the latter over the former. Stop drivelling on without a point". OK OK. Let me give you an example of why I made the switch (Note that this is one of many reasons), Here's the first in MySQL:

{% highlight sql %}
mysql> CREATE USER 'foo';
Query OK, 0 rows affected (0.00 sec)

mysql> CREATE USER 'foo';
ERROR 1396 (HY000): Operation CREATE USER failed for 'foo'@'%'
{% endhighlight %}

Hmm OK, ERROR 1396.. That sounds precarious. Of course these operations only really make sense when they're not executed one after another. Now this may be clear to you.. but c'mon, that's a shit error message, lets be honest. Let's look at the same code in PostgreSQL:

{% highlight sql %}
injekt=# CREATE USER "foo";
CREATE ROLE

injekt=# CREATE USER "foo";
ERROR:  role "foo" already exists
{% endhighlight %}

Ah yes! The role "foo" already exists, so it's failed. Awesome! Now I don't have to Google the error or think about remembering a bunch of predefined error codes. That's productive! Moving on..

{% highlight sql %}
mysql> CREATE TABLE test (id tinyint);
Query OK, 0 rows affected (0.07 sec)

mysql> INSERT INTO test VALUES (700);
Query OK, 1 row affected, 1 warning (0.00 sec)
{% endhighlight %}

Ok wait.. that worked fine, it shouldn't have worked fine.. but it did. Oh look, 1 warning.. That's useful, so my program runs without errors, and now I have to search around for 'warnings'. Thanks, MySQL!

I could possibly do this all day, so if you want more examples, perhaps take a look at [A Follow Up on the SQL puzzle](http://www.joinfu.com/2010/03/a-follow-up-on-the-sql-puzzle/).

Another bugbear I have is something developers have become akin to, tab completion! I mean c'mon, it's everywhere. Bash (with extensions), Zsh, even Irssi. Oh **AND** PostgreSQL. So why does the MySQL clients tab completion, or lack of, suck so bad?

If anyone has any insightful information, perhaps some examples which directly contradict my findings, or better yet examples which prove my point more so, please share. I'd love to see many more examples or generally hear peoples thoughts on this.

**PS**: If you've just written half a blog post and accidentally close the tab in Firefox, rather than raging for about 10 minutes and wanting to hurt something cute and fluffy. Just hit Control+Shift+T and your tab will magically appear from the depths of the underworld. Thank god.
