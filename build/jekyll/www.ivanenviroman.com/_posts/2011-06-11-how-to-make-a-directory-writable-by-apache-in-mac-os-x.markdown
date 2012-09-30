---
comments: false
date: 2011-06-11 16:56:06
layout: post
slug: how-to-make-a-directory-writable-by-apache-in-mac-os-x
title: How to make a directory writable by Apache in Mac OS X
wordpress_id: 2301
categories:
- Bookmarks
tags:
- apache
- filepermissions
- macosx
---


                
                    Whenever I begin work on a new web development project, I seem to always have trouble remembering how to make a directory writable by Apache in Mac OS without giving full rwx permissions to everyone.

Here is a quick reference for myself and anyone else who runs into the same issue.

Set the ownership of the directory to the _www user which Apache runs under in Mac OS:

# chown -R _www:staff cache

Set the appropriate permissions so that the _www user can write, without giving unnecessary permissions to everyone else:

# chmod -R 755 cache

And voila, no more dreaded warning messages about directories not being writable.
                
            
