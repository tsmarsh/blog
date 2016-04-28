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

Current DRM aims to model the existing physical solutions of disks and
tapes where copying the physical media is both cumbersome and
unlawful. They do this by selling you the medium encrypted into
garbage and devices with a key that transform the garabage into the
medium for you entertainment.

But the problem is that they still had to sell you a key, and that at
somepoint you have to decrypt the garbage, rendering any encryption
moot. So we have the DMCA that fills the legal holes making it
unlawful to decrypt the content outside of the systems distributed by
copyright holders.

That is, you are breaking the DMCA if you decided to make an
unencrypted backup for the media you purchased, or if you decided to
format it for a device that doesn't have the key.

Both of these are clearly enhancements to the deal distributers had
back with physical media. Particularly the second part. The key, in
this new world, is frequenty associated not with the medium or its
quality, but with the store where you bought it. So if you want to
watch a movie you purchased at Apple on a device made by Google you
have to repurchase the content at a Google store.

Great deal for content creators, but this is a horrible deal for
consumers. Why shouldn't I be able to lend my copy of a movie to a
family member? Why shouldn't I be able to keep a copy of a bluray on
my network so I can more easily appreciate its contents? Why should I
have to repurchase a movie just because I decided that I didn't like
my phone?

The current answer is: "Because if we allowed that, its far too easy
for people to get the content without paying for it."

Responsible members of society must understand that it costs time and
money to create content. Not only that, the risks associated with
making that content are really high. The chances of making your money
back are already pretty low. If you want to watch a movie you should
have to pay for it. 

But the problem here is that preventing a copy from occuring is
impossible in the digital world. Copying is all they do. Transfering or
distribution is really just copying. When you watch a Bluray the
images aren't transfered to the screen they are copied to the screen,
for some period a portion of the movie will exist on the screen,
cable, video decoder, ram and the original media. Perfect copies.

If you were to 'lend' your copy of a movie to a family member you
would still have your copy. There would be nothing stopping you from
watching it at the same time, and no reason for the family member to
give you a copy back. Same for backups, what happens if you sell the
harddrive with the backups on it? What happens if you put your backups
in the cloud and your account gets hacked? Why should the content
creators suffer in these situations?

Well thats the thing... nothing, at the moment. 

The other thing computers do really, really well is identity.
Computers are excellent at the complex math that backs encryption
algorithms that prove that a given message was sent by given entity.

What we're proposing is a shift away from copy prevention (an
impossible task given that computing is copying), to ownership
verification, something that computers are actually good at.

## Step 1 - Fingerprinting

A movie is 30-60fps of a grid of pixels being hurled at your eye
balls. It is trivial to create an undetectable fingerprint in the
movie by swapping frames, adding new b-frames, you can even switch
pixels. You can do the same with audio tracks, you can swap
inperceptably individual integers in the wav and create
imperceptable differences in the sound. The only way to extract them
would be to diff the original (which could be treated as a secret). 

Creating a fingerprinted copy at the point of sale for an individual
should be easy.

How the fingerprinting is done is not important. It can vary from
content producer to content producer. 

A cryptographic hash of the movie can then serve as the fingerprint.

Of course most content is compressed using 'lossy' algorithms that are
designed to smooth out or remove the kind of inperfections that I'm
talking about. In those instances it is probably approriate to simply
put you public key in the metadata and then sha the file. 

## Step 2 - Content Identification

We have the Shazam [algorithm](https://www.toptal.com/algorithms/shazam-it-music-processing-fingerprinting-and-recognition) for identifying sound track. There are
similar algorithms for movies too. What we're looking for here is an
algorithm that can identify the source material of a fingerprinted
copy regardless of the play back medium, quality or compression.

## Step 3 - User Identification

Thanks to projects like [Keybase](https://keybase.io) it is now much
easier for people to create secure, and verifiable encryption keys.
Using services like this we can use a 4096bit key to identify a
customer. 

Something like an RSA keypair is import so that you can not only
transfer blocks of data without fear of eavesdropping, but also as a
mechnasim for verfying that the data was sent/created by whom you
believe it was sent by.

## Step 4 - A Registry

So now all we need to do is combine these three data into a single,
shared database.

The purpose of this registry will be to prove that you have paid for
content or have in some other manner aquired legitimate rights to the
content. 

If you are raided by the police and your assets are searched, a third
party can verify that and content they find on your system belongs to
you by:

1. Running the content identification algorithm
2. Finding your public key next to the sha of the content

But what about the fingerprint. That is to help find where the content
has come from. If you transform the content say from H.264 to H.265
you need to re-fingerprint and log that in that registry, creating a
link between your original purchase and this particular copy and the
prevent accusations of theft. 

If you transfer ownership of one copy, you will also forfit you right
to your copies. A little personal responsibility will be required for
you to delete copies you no longer own, but honestly that could be
managed by play devices that simply warn or refuse to play content
that you don't own. 

## Step 5 - Block Chain

So who should hold this registry? The government? The studios? I'd say
everyone. 

The recent change in Computer Science that makes it possible
for multiple, identical copies of a database to exist is [Block Chain](https://en.m.wikipedia.org/wiki/Block_chain_(database)),
the technology behind [BitCoin](https://bitcoin.org/en/).

What would that look like? 

Just like bitcoin you would have the choice of keeping and maintaining
your own copy of the block chain, or you could use a service and
submit changes or ask for verification. 

## Step 6 -Enforcement

If you are suspected of dealing or receiving unlawful copies of a
movies your assets a warrant could be obtained and search of your, or
your clients data may turn up media that doesn't have your key next to
the hash of the content, and you'd be in bad shape if you have content
that you own but that you haven't re-watermarked and commited to the
registry. 

## Questions

### What about personal movies? 

Thats up to you. But adding them to the registry would enable to claim
ownership. I could see this being very useful for content containing
your children, that you may want to share, or give to a relative, but
would feel uncomfortable if they were found in the hands of strangers.
This would at least allow you to see who transferred the photos. 

### What if the content is modified beyond the capabilities of the
identification algorithm?

This is already common on platforms like
[YouTube](https://youtube.com) which already the contents of
their servers using identification algorithms. At that point it becomes the
job of conventional law enforcement and the original content holders,
much as it is today. 

Remember, it is legal, and in many ways encouraged for works of art to
be inspired by others and it is protected by fair-use. This will
continue to be solved by traditional legal channels. 

### How do we start?

I don't think we'd need permission from the studios to just do this.
It could start as a 'grass roots' project. Where individuals register
their purchases in a global registry.

It would be interesting to test the legality of a transfer made in
this manner. It would violate the DMCA, but it is well within the
bounds of conventional copyright. Given the DMCAs age and popularity,
proving this as a viable alternative to DRM could be really
interesting. 
