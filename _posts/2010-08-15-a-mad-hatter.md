---
layout: post
title: A mad hatter
---

## A mad hatter

Damn it's been over a week since I last posted, I totally suck at this blogging thing. I hope you all (like, the 3 people who read this blog) forgive me, and accept my dearest apologies and many internet cookies (no pun intended).

So, remember the triangular present which totally couldn't be a guitar? Well, IT WAS A GUITAR! Woo etc. I've been hinting about starting to play again for quite some months. I guess my ongoing twaddling doesn't go totally unnoticed. I'll post some pictures some time later this week, it's really pretty looking!

On another note, Cinch is about to be released as version 1.0.0! Time is almost there, and it's pretty exciting. Once I have gotten around to writing up the specifications a release is on the cards. Although I'm thinking that may take some time, so it could be before I finish them (ssh, don't tell anyone). Dominik has done a great job on the examples and twiddling the odds bits of Cinch, it's looking really great.

So I told you guys I've started using [zsh](http://www.zsh.org/). Yep, that's right! It's super duper delicious-ness makes me all warm inside.  I've now managed to remove over 300 lines of bash code, and 3 bash completion files! Zsh makes completion it's bitch, it's pretty wonderful. Here's my sparkly new .zshrc:

{% highlight bash %}
#!/bin/zsh

# Skip all this for non-interactive shells
[[ -z "$PS1" ]] && return

# completion
autoload -U compinit
compinit

# ./ssh/config hostname completion
if [ -s "$HOME/.ssh/config" ]; then
  hosts=(`hostname` `grep "Host " ~/.ssh/config | cut -d " " -f2`)
  zstyle '*' hosts $hosts
fi

# history
HISTSIZE=2000
HISTFILE="$HOME/.histfile"
SAVEHIST=$HISTSIZE

setopt hist_ignore_all_dups # ignore history duplicates
setopt autocd # cd is just 2 many characters, har
setopt extendedglob # sex

alias ls='ls --color'
alias grep='grep --color'
alias mkdir='mkdir -p'
alias g='2>/dev/null gvim --servername vroom --remote-tab'

# Set PS1 with colour dependant on hostname
local red="%{"$'[1;31m'"%}"
local green="%{"$'[1;32m'"%}"
local yellow="%{"$'[1;33m'"%}"
local none="%{"$'[0m'"%}"
local colour
case `hostname` in
  "bebop") colour=$yellow ;;
"bernard") colour=$green ;;
        *) colour=$red ;;
esac
PS1="[${colour}%~${none}] %% "

# Add our ~/bin directory to the PATH
[[ -d "$HOME/bin" ]] && PATH="$HOME/bin:$PATH"

# rvm baybee
[[ -s "/usr/local/rvm/scripts/rvm" ]] && source "/usr/local/rvm/scripts/rvm"
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
{% endhighlight %}

If anyone has any neat tips/tricks they know of, please let me know. I'm still pretty new to it. I've also revised my `.vimrc` too! It looks a little like this:

{% highlight bash %}
" bad vi!
set nocompatible

" continuous indentation
set autoindent
set smartindent

" match corresponding brace/parenthesis
set showmatch

" allow backspacing over everything in insert mode
set backspace=indent,eol,start

set nobackup            " dont keep backup files
set noswapfile          " ugh
set history=300         " history buffer
set ruler       " show the cursor position all the time
set showcmd     " display incomplete commands
set incsearch       " do incremental searching
set shiftwidth=2        " 2 is enough
set tabstop=2
set smarttab            " <3 smart tabbing
set expandtab           " correct spaces
set autoread            " auto read file when it's changed/updated
set title               " allow vim to change the title
set number              " we like line numbers
set nohlsearch          " dont hilight search words
set ignorecase          " ignore case when searching
tab all

" Control+W to close a tab
map <C-w> :tabclose<CR>
" Control+T to open a new tab
map <C-t> :tabnew<CR>

" Alt + left/right key for switching tabs
map <a-left> :tabp<CR>
map <a-right> :tabn<CR>

" if we're using gvim
if has("gui_running")
  set guioptions-=T   " remove gvim toolbar
  set lines=40
  set columns=100
  winpos 600 30       " window geometry

  colorscheme desert

  " Control + S for saving
  noremap <C-S> :update<CR>
  vnoremap <C-S> <C-C>:update<CR>
  inoremap <C-S> <C-O>:update<CR>
endif

" In many terminal emulators the mouse works just fine, thus enable it.
if has('mouse')
  set mouse=a
endif

" make sure we switch syntax highlighting on if
" we have colours! yadaboi
if &t_Co > 2
  syntax on
endif

" Only do this part when compiled with support for autocommands.
if has("autocmd")
  " Enable file type detection.
  " Also load indent files, to automatically do language-dependent indenting
  filetype plugin indent on
endif
{% endhighlight %}

Again if anyone has any super awesome tricks, let me know! I've been using vim for quite some time now, but I still find myself hanging onto the handbooks every word so often.

On an unrelated note, I've been re-learning [Haskell](http://www.haskell.org/) the past couple of weeks. I really really recommend the **Learn you a Haskell for Great Good!** book, it's pretty darn awesome. Check it out [here](http://learnyouahaskell.com/). It can be a little scary for object oriented programmers but you'll get the hang of it quickly and realize how powerful it can be, if not a little bonkers.

I promise to update this blog a little more!