---
layout: post
title: SSH Host Completion
---

## SSH Host Completion

If you're like me and enjoy bash-completion so much you want every application to take advantage of it, or perhaps you numerous hosts you send/receive data to and from via SSH, read on..

If you're not, you can also read on if you'd like. I may provide some pretty pictures or a treat at the end of this entry just for you guys. I'm nice like that.

Are you like me and take advantage of the `.ssh/config` file?

1. No, that sounds interesting though...
2. Yes, I <3 `.ssh/config`
3. No, I don't like it, go away, I'm navigating away from your graceful yet fruitless blog right now
<p></p>
* If you answered 1, see [here](http://linux.die.net/man/5/ssh_config). It's awesome!
* If you answered 2, read on
* If you answered 3.... :-(

So.. Here's a quick example of what my `.ssh/config` file looks like:

{% highlight text %}
Host phillip
    HostName foobar.net
    Port 8927
    User lee
    IdentityFile ~/.ssh/id_rsa.pub

Host injekt
    HostName injekt.net
    Port 2322
    User injekt
    IdentityFile ~/.ssh/id_rsa.pub

Host scooby
    HostName scooby.doo
    Port 2211
    User daphne
    IdentityFile ~/.ssh/id_rsa.pub

Host flamingo
    HostName 11.234.21.234
    User fred
    IdentityFile ~/.ssh_id_rsa.pub
{% endhighlight %}


Now of course, this isn't what my `.ssh/config` file looks like at all. Though I'm sure the employers I work for would not appreciate their SSH login credentials spread across my blog, so I have replaced the entries with clearly meaningful duplicates.

Ok so now all we have to do to login to foobar.net is this: `ssh phillip` Great, isn't it? This even works with SCP, and of course Git over SSH.

Now have you ever tried to do this: ssh ph[tab] ? Because.. I have.. many times.

Throw the following code into a file named .ssh-completion or directly into your `.bashrc` or `.bash_profile`:

{% highlight bash %}
_complete_ssh_hosts () {
  COMPREPLY=()
  cur="${COMP_WORDS[COMP_CWORD]}"
  comp_ssh_hosts=`
    if [ -f ~/.ssh/config ]; then
      cat ~/.ssh/config |       grep "^Host " |       awk '{print $2}'
    fi
  `
  COMPREPLY=( $(compgen -W "${comp_ssh_hosts}" -- $cur))
  return 0
}
complete -F _complete_ssh_hosts ssh
 {% endhighlight %}

If you put this into a file named `.ssh-completion` make sure you add `source ~/.ssh-completion` to your `.bashrc` file.

Reload your terminal, and walla! It just works..

PS: if it doesn't, it's not my fault

Oh and for those of you who have waited all this time just for the treat or pretty picture, don't worry I haven't forgotten...

PS: I would quote the original source of the SSH completion script but I have no idea what it was, it was a while ago. If anyone has an idea please let me know and I shall update this entry accordingly.