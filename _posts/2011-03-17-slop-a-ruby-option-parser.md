---
layout: post
title: Slop - A Ruby option parser
---

## Slop - A Ruby option parser

I recently **re-**released [Slop](http://github.com/injekt/slop). I say re-released because the original release of Slop happened more than [3 months ago](https://github.com/injekt/slop/commit/1c9367b2e765bb6e6f215f4bcc9c9b7bf1456166). The reason I had originally started to write Slop was to solve some *issues* I had come across in some private projects I'm involved in contributing to.

Unfortunately for Slop, half way through development the topic changed and I lacked the motivation to put effort into something I wouldn't be using much. The outcome? Releasing a half baked turd of a library.

No, seriously.

After starting another project which involved a command line interface, I thought... I know, this is a job for **Slop!** Boy was I wrong. Issue after issue arose, even the most basic logical functionality didn't work. Blocks weren't executed where or when they should be, return data was painfully random, and the help output string building algorithm was over thought and fatiguing. It was a true disaster.

This library was featured on Rubyflow, Ruby5, and had around 50 followers on GitHub by this point. Nothing major, but enough publicity to start some smalltalk. I even [blogged about it](http://lee.jarvis.co/sloppy-option-parsing). Clearly none of these people **actually used it**. Otherwise someone would have punched me in the face a long time before I had found these issues out myself.

So I decided I should rewrite it. I mean rewrite **all** of it. The first major commit was [this one](https://github.com/injekt/slop/commit/4ffcafec73f2c15f47f9d49fe58cfd0cae63c7c9) which included 259 deletions (one file). Followed by [this one](https://github.com/injekt/slop/commit/9041450ccc6cc64422268ae75ba64ad2996546db) which started the foundation. Since then 2 days passed and I had a stable release I was actually happy with.

From this I realized I should be using my own projects more often, writing 100% test coverage and making sure that my tests define a specification, my code must reach the standards of my testing, not the other way around.

Tell me what you think of Slop.