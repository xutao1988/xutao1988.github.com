---
layout: post
title: All up in your Epoxy
---

## All up in your Epoxy

Epoxy is a binding API for querying databases. It handles:

1. ?name for named binds
2. ? for numbered binds
3. ?? for a real question mark
4. '?' for a real question mark
5. Comments, weird quoting styles
6. It won't tell you how to quote your data. This solution works for any query language and any database.

Want an example? Sure thing..

{% highlight ruby %}
# numbered binds
ep = Epoxy.new("select * from foo where bar=?")
binds = %W[foo]
bound_query = ep.quote { |x| "'" + binds[x] + "'" }
"select * from foo where bar='foo'"

# named binds
binds = { :name => 'Lee', :age => 132 }
ep = Epoxy.new("select * from people where name=?name and age=?age")
bound_query = ep.quote(binds) { |x| "'#{binds[x]}'" }
"select * from people where name='Lee' and age='132'"

# mix them!
binds = { 0 => "Age", :name => 'Lee' }
ep = Epoxy.new("select * from people where name=?name and age=?")
bound_query = ep.quote(binds) { |x| "'#{binds[x]}'" }
"select * from people where name='Lee' and age='Age'"
{% endhighlight %}

Neat, right? here's a real demo using the PG RubyGem:

{% highlight ruby %}
#!/usr/bin/env ruby

require 'epoxy'
require 'pg'
require 'ap'

conn = PGconn.open(:dbname => 'rdbi', :user => 'rdbi')

conn.exec("DROP TABLE IF EXISTS users")
conn.exec("CREATE TABLE users ( id SERIAL PRIMARY KEY, name VARCHAR, pass VARCHAR )")

queries = [
  { :name => 'Lee', :pass => 'foo bar' },
  { :name => 'injekt', :pass => 'bar baz' },
  { :name => 'steve', :pass => 'lorem e' },
]

queries.map! do |q|
  quote = proc { |n| "'#{q[n]}'" }

  ep = Epoxy.new("INSERT INTO users ( name, pass ) values ( ?name, md5(?pass) )")

  ep.quote(q, &quote)
end

ap queries
{% endhighlight %}

Which provides the following output:

{% highlight ruby %}
[
	[0] "INSERT INTO users ( name, pass ) values ( 'Lee', md5('foo bar') )",
	[1] "INSERT INTO users ( name, pass ) values ( 'injekt', md5('bar baz') )",
	[2] "INSERT INTO users ( name, pass ) values ( 'steve', md5('lorem e') )"
]
{% endhighlight %}

Epoxy is the latest release from the RDBI team.

* Use Epoxy
* Profit
* Repeat