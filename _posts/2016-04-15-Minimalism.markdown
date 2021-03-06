---
layout: post
title: "Minimalism"
date: 2016-04-15 09:00
comments: true
categories: [dev]
---

I realized a couple of days ago that I only had two applications open:

* A terminal - I use iTerm on OSX, but any 256 color terminal is fine
* A browser - I use Chrome, mostly because it works well on Linux, OSX
  and Windows. 

<!-- more -->

These two applications now cover 100% of my computing needs.

# Terminal
* Emacs
  * Coding
  * Blogging
  * Sys admin
  * Org mode
  * Magit 
* SSH
  * Remote sys admin
  * Tunneling (making remote services feel local)
* tmux
  * Pairing (close to 0 lag, no compression artifacts)
  * Session keep alive
* Vi(m) (When emacs isn't installed)

# Browser
* Slack / Hipchat 
  * Primary mechanasim for team chat
  * Keeping up with old friends
  * Dramatically reducing email load
* Gmail
  * Looking to kick this soon and start using emacs for mail, mostly so
I can start using PGP more.
* Site that I'm building 
* Monitoring
  * Currently enjoying the ELK stack
* Research

Thats it. 

A couple of functions have moved to my phone, mostly my calendar.

So why bother?

*Flexibility:* As long as the platform supports a terminal and a browser
I can be incredibly productive. This week I found out that Android has
Temux, which exposes enough of the underlying linux to enable me to
run my full emacs profile. I am now as productive on my phone as I am
on Windows. 

*Text:* Every thing is better if you can edit it in as a text file. You
get to use Emacs to edit it, you get to use Git for version control,
you can comfortably work with it over SSH and you can have mobs of
devs work with you over tmux. And thats just the terminal. Text is the
founding technology behind the web too.

*Shortcuts:* There is a technology underpinning the shortcuts of shells,
REPLs, text boxes (on osx... seriously linux, you should get this) and
a surprising number of web apps called readline. Readline uses, mostly,
the same shortcuts for navigation as emacs. Learn emacs, and all of a
sudden you can edit like a pro everywhere.

*Pramatism:* As much as I think emacs should be taught a long side
learning to type, I'm not going to win that argument. If I was
building a new service (and that is what I do for a living), I'm going
to target the web and not emacs, although after using the Bloomberg
Terminal I do wonder if I'm right. The web is a wonderful, lightweight
way of accessing other peoples services. I could move a lot of what I
use a browser for into Emacs, perhaps I should for text based things
like Slack and email, but I probably won't.

Mostly, though there is a feeling of using the right tool. Everything
is easier. 

Text interfaces might not be pretty and they might be harder at first,
but you really only have to learn them once, and then everything else
is easier. 
