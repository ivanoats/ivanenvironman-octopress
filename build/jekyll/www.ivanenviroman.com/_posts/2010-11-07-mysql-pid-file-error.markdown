---
comments: true
date: 2010-11-07 09:54:07
layout: post
slug: mysql-pid-file-error
title: 'How to resolve MySQL: ERROR! Manager of pid-file quit without updating file'
wordpress_id: 1863
categories:
- software
tags:
- homebrew
- mac
- mysql
---

This probably only applies if you are setting up MySQL via [homebrew](https://github.com/mxcl/homebrew) on your mac.

I ran the normal `brew install mysql` then found this error: `ERROR! Manager of pid-file quit without updating file`.

It turns out the solution was that I had missed part of the install instructions. Make sure to `brew info mysql` if you missed it after mysql installs. It contains the instruction you probably missed to `mysql_install_db`

Getting the database set up properly resolved the error for me.

UPDATE: After upgrading to Mac OS 10.6.5, I had the same error. I was stumped, until I realized that Apple's update had changed the write permissions on /usr/local I ran `sudo chmod g+w /usr/local` and then restarted mysql, and it worked!
