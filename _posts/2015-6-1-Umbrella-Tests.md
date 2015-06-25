---
layout: post
title: "Umbrella Tests"
date: 2015-6-1 09:00
comments: true
categories: [QA]
---

I would like to propose that automated ui testing be called "Umbrella
Testing" from this point forward.

Imagine that your software is a nice suit. You are so proud of this
suit that you got your nails did and your hair is on point. You want
to take it to the world. The weather report is clear, but you know that if its going to rain, its going to be on demo
day. What do you do?!

Reach for your poncho my friends, reach for your poncho.

<!-- more -->

> um·brel·la
>
> /ˌəmˈbrelə/
>
> _noun_
>
> 1. a device consisting of a circular canopy of cloth on a folding metal frame supported by a central rod, used as protection against rain or sometimes sun.
> synonyms:	parasol, sunshade
> "they huddled under the umbrella"
> 2. a protecting force or influence.
> "the American nuclear umbrella over the West"

UI testing should fall under the second definition of umbrella: a
protecting force or influence, but invariably resembles the first.

What is wrong with that? Umbrellas don't work.

![umbrella fail](http://cdn.coresites.factorymedia.com/mpora_new/wp-content/uploads/2015/02/Windy.jpg)

At least they only work if it is raining in a particular way, straight down, with little wind.
Even if they are working correctly they cause more problems than they are worth,
with reduced visibility, significant chance of having them blow away,
and a dramatic increase in the number of sharp pokey things at eye height.

You see the problem is that umbrellas are sold as if had the
properties of the second definition, which would only be possible if there
was an invisible force field that let air through and kept rain out
and that is clearly impossible.

![the impossible dream](http://www.qmuniforms.com/photos/styles/RW114_330_1.JPG
 "The Impossible Dream")

My position is this: UI testing is like an umbrella.

It does work, but only when the
heavens are aligned. So only plan to use them for drizzle protection
(minor regression failures), and buy cheap, because its going to break
as soon as you really need it. When they do break, use a poncho. Which is
why, even if you did buy an umbrella, you should always carry a
poncho... unless keeping dry isn't your reason for using an umbrella.

Some people have umbrellas so that, when they show up looking bedraggled,
they can say "At least I used an umbrella". They know that umbrellas
don't work; the people they are talking to know that umbrellas don't
work but there is some acknowlegement that something was tried and due
diligence was done. The level of due diligence required will
depend greatly on your industry.

So what are "Poncho Tests"?

[Service tests](http://martinfowler.com/bliki/TestPyramid.html). That
is you test everything but the UI. You test that the business logic
integrates, messages pass along the full stack, you might even talk to
a database. But you don't even look at the UI. Why?

Its faster and more reliable this way. Poncho tests are smaller,
lighter and involve much less training than umbrella tests and have the interesting property of doing a better job than.

Just as it is ok to use an umbrella with a poncho if your hair is
particularly important to you, it is ok to use umbrella tests with
poncho tests.

You can get away without carrying a poncho. It is fun to live
dangerously. But when it rains you will look like an idiot.

So what are unit tests?

![Undies!](https://www.eslpod.com/eslpod_blog/wp-content/uploads/2015/02/JockeyUnderwear635.jpg
"Don't leave home without them")

Underwear Tests. You use them everyday regardless of the weather
because they are not about keeping you dry or warm, they are about
reducing smells. They are changed frequently, but ultimately nobody cares as they are hidden
under your business clothes. They are cheap and disposable because...
shit happens.

If you are not sure if your test is a underwear or a poncho test, you
may have accidently wrapped your business logic in a "diaper test". Rails
'unit tests': I'm looking at you.

