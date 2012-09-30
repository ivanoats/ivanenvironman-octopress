---
comments: true
date: 2010-10-24 22:10:48
layout: post
slug: macports-to-homebrew
title: Macports to Homebrew
wordpress_id: 1834
categories:
- Bookmarks
tags:
- homebrew
- imagemagic
- mac
- rmagick
---

I'm now recommending using [Homebrew](https://github.com/mxcl/homebrew) instead of [MacPorts](http://www.macports.org/) to install all the various unix-y utilities a mac developer needs. Here's my current "brew list"

    
    <code>
    ivan@tremuloides:17:23:36:~> brew list
    ack		imagemagick	libtiff		memcached	tokyo-cabinet
    ctags		jasper		libxml2		mutt		tree
    dos2unix	jpeg		links		php		watch
    gettext		libevent	little-cms	pkg-config	wget
    ghostscript	libpng		mcrypt		rubinius	xdebug
    </code>




Tip: Joe Johnston on Simple10.com says "I’m not sure if it’s possible to install ghostscript and imagemagick without using sudo."
