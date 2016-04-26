---
layout: post
title: "Fixing DRM"
date: 2016-04-15 09:00
comments: true
categories: [dev]
---

[Michael Baker](http://michaelbaker.sexy) and I, without the aid of
libations went a good way to fixing DRM today, albeit in the best way
possible: in theory.

We posit that, rather than focussing on preventing copying, we focus
on making it trivial to prove that you have the access rights to a
given piece of media and really hard to fake legitimate access rights. 

This is very different from current DRM. 

Current DRM assumes that you are a criminal and that all copying in
someway dimminishes the profits of the content creators.
[Cory Doctorow](https://craphound.com) does a much better job than I
ever will on explaining why DRM is a fundamentally bad idea.

But I think we have by now experienced the downsides of DRM. You may
have been in love with Apple in the iPhone era, but as smart phones
have opened up, Windows has started to suck less and linux become more
viable every day sticking to one platform, especially the Apple
platform exclusively is folly. You can only watch your HD iTunes
movies if you have a HDMI cable a device that is 'secure', you can
only watch you iTunes movies on Apple approved devices and whilst that
includes Windows computers it sure as hell doesn't include XBMC,
Linux, Android, Windows Phone or Roku... the list goes on.

And that is by design. Content producers would like to think of the
Apple Store as BluRay, Youtube as DVD and Google Play as HD-DVD. If
you want to watch on your new player, you have to buy a new copy. That
was pretty jarring during the switch from vinyl records to CD, in this
era of differing DRM wrappers around the same H.264 bitstream, its
robbery.

What we're proposing is a shift away from copy prevention (an
impossible task given that computing is copying), to ownership
verification.

## Step 1 - Fingerprinting

A movie is 30-60fps of a grid of pixels being hurled at your eye
balls. It is trivial to create an undetectable fingerprint in the
movie by swapping frames, adding new b-frames, you can even switch
pixels. You can do the same with audio tracks, you can swap
inperceptably switch individual integers in the wav and create
imperceptable differences in the sound. The only way to extract them
would be to diff the original (which could be treated as a secret). 

Creating a fingerprinted copy at the point of sale for an individual
should be easy.

How the fingerprinting is done is not important. It can vary from
content producer to content producer. 

A cryptographic hash of the movie can then serve as the fingerprint.

## Step 2 - Content Identification

We have the Shazam algorithm for identifying sound track. There are
similar algorithms for movies too. What we're looking for here is an
algorithm that can identify the source material of a fingerprinted
copy. 

## Step 3 - User Identification

Thanks to projects like [Keybase](https://keybase.io) it is now much
easier for people to create secure, and verifiable encryption keys.
Using services like this we can use a 4096bit key to identify a
customer. 

## Step 4 - A Registry

So now all we need to do is combine these three data into a single,
shared database.

The purpose of this registry will be to prove that you have paid for
content or have in some other manner aquired legitimate rights to the
content. 

The purpose of this is to that if you are raided by the police and
your assets iindare searched, a third party can repeatedly verify that and
content they find on your system belongs to you by:

1. Running the content identification algorithm
2. Finding your public key next to the sha of the content

But what about the fingerprint. That is to help find where the content
has come from. 

## Step 5 - Block Chain


