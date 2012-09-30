---
comments: true
date: 2009-02-14 17:04:57
layout: post
slug: render-error-when-upgrading-from-rails-1-to-rails-2
title: Render error when upgrading from rails 1 to rails 2
wordpress_id: 475
categories:
- rubyonrails
tags:
- footnotes
- rails
- ror
- rubyonrails
- textmate
---

When upgrading an old ruby on rails 1.2 application to rails 2.2.2, I ran into a frustrating, somewhat un-google-able error, so I'm writing down the solution here.

If you get a render with invalid options error,  the solution is to uninstall the textmate footnotes plugin, and use the rails-footnotes plugin instead.

Thanks to[ David Zohrob's blog post](http://blog.zohrob.com/?p=29) for helping me figure this out.
