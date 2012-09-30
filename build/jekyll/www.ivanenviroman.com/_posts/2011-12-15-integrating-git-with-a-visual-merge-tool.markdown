---
comments: false
date: 2011-12-15 16:16:52
layout: post
slug: integrating-git-with-a-visual-merge-tool
title: Integrating Git with a Visual Merge Tool
wordpress_id: 2556
categories:
- Bookmarks
tags:
- git
- mac
- rubyonrails
---

One of the first real points of frustration a developer encounters with Git is the initial unresolved merge conflict.  And it’s only a matter of when, and not if, it will happen.

The root cause of the conflicts is unavoidable in any kind of parallel development: Updates that are made independently may modify the same or overlapping regions of the codebase.  The longer the development remains independent, the greater the probability this will take place.  For a tool that is basically based on branching and parallelism, Git is essentially inviting this “trouble.”  (Rest assured that the benefits are still well worth it.)
