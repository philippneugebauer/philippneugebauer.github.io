---
layout: post
title:  Gem for building native compilation for all platforms
date:   2015-03-10 23:30:00
categories: ruby vagrant native-compilation windows
---

By trying to set up my windows development environment for GitterGlitter to get known to a possible project for the Google Summer of Code,
I was struggling a lot with the native compilation of the rugged gem. I tried several methods proposed by blogs and StackOverflow to compile it
on windows but I couldn't resolve all the problems. Lastly, I found the amazing [rake-compiler-dev-box gem](https://github.com/tjschuck/rake-compiler-dev-box)
which seemed to be a great opportunity to resolve all my problems and also provide a great solution for my next compilations.

It allows to easily compile required gems and to install it on all platforms. Although I'm still struggling with the setup and I
reported an issue to the gem developers, I just can recommend this great gem to you.

While struggling with Rake Compiler Dev Box, I also encountered [this information](http://kvz.io/blog/2013/01/16/vagrant-tip-keep-virtualbox-guest-additions-in-sync/)
useful to avoid the annyoing update warning of vagrant.
