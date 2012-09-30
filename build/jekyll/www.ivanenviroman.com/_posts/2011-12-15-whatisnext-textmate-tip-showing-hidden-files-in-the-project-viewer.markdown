---
comments: false
date: 2011-12-15 16:17:08
layout: post
slug: whatisnext-textmate-tip-showing-hidden-files-in-the-project-viewer
title: 'whatisnext - Textmate Tip: Showing hidden files in the project viewer'
wordpress_id: 2521
categories:
- Bookmarks
tags:
- git
- textmate
---

Show .gitignore in project file list. In Textmate, goto Preferences -> Advanced. Then change the beginning of the File Pattern from:

(?!htaccess)
To:

(?!(htaccess|git*))
