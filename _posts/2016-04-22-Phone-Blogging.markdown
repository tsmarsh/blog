---
layout: post
title: "Phone Blogging"
date: 2016-04-22 19:33
comments: true
categories:
---

Blogging from my phone is nothing new. I've been connecting my trusty
[K760](http://support.logitech.com/en_gb/product/wireless-solar-keyboard-k760-for-mac)
for a while. But... apps. 

I was as excited as anyone when Steve Job's
introduced the idea of mobile apps. I like small, single purpose
applications that do one thing well, but that thing is rarely text
entry and even pointing is very imprecise. 

Screen keyboards are a lot better than
[T9](https://en.m.wikipedia.org/wiki/T9_(predictive_text)), but that
really doesn't say very much. So, we've built apps around
the idea that people aren't going to type, or, do anything other than
consume.

Here is my litany of complaints about the apps I've used for blogging
on my phone:

* They're just text editors and getting text out of them is involved
* They're designed for one service and I don't want to use that service
* They're designed for one service, which is good, but they're
  terrible editors. 
* They're not emacs

Phones are still really interesting as a platform. They are tiny, they
have great screens, they have an internet connection and they're
getting more powerful every year. Also, my phone is with me
constantly - so turning it into something that I can create on, in
addition to consume is appealing. 

But they're still incredibly slow compared to laptops, at least the
laptops of today, but its a super computer compared to technology from
30 years ago. 

So what happens when we treat our 2016 phones like 1986 desktop
computers. 

Turns out, really, really good things. Text interfaces work really
well, especially in landscape mode. Plus, even with a bad connection,
SSH and git work surprisingly well. 

So what does this old/new world look like?

My Android phone is a linux kernal wrapped in a finger friendly GUI.
[Termux](https://termux.com) peels away the GUI and leaves me with a
very useful terminal emulator.

This is all well and good. It has allowed me to ssh into my servers,
which is neat but not exactly worth carrying a keyboard around for.

But recently it got Emacs.
[Emacs!](https://www.gnu.org/software/emacs/). The one true editor. To
Emacs, my phone is like a palace. It was first created when 80
charactors was widescreen, when 256 colours was 254 too many. Emacs,
an editor who's one true purpose is to be the true interface to every
single text file you have ever edited. And its not Emacs 'lite', its
full emacs, so full that I can use
[Outpace Starter Kit](https://github.com/outpace/emacs.d), which is
what I use every day for real software developement.

Not only can I edit text files, termux also has
[git](https://git-scm.com), and [tmate](https://tmux.github.io) so I
can share text files and pair with people, just like a 'real'
computer. 

So, here I am, editing a blog on a device that fits in my pocket, on a
full sized [keyboard](http://www.logitech.com/en-us/product/multi-device-keyboard-k480),
that weighs next to nothing, and has a cute slot for my phone to stand
in and I have editting power comparable to my beloved MacBook Pro
(which doesn't have built in LTE). 

It is not ok to call this the future. There is nothing novel about using
small, under powered computers for text editing. But I do feel that it
drives home, once again, that investing time in learning a technology
like terminal emulators, ssh and emacs/vi is rarely time wasted.

Now the only problem is that the lovely screen in my phone is almost
as useless in daylight as my laptop... I wonder if I can get emacs
running on a kindle. 
