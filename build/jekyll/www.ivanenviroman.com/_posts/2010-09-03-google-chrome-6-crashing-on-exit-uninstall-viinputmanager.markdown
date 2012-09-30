---
comments: true
date: 2010-09-03 20:03:45
layout: post
slug: google-chrome-6-crashing-on-exit-uninstall-viinputmanager
title: Google Chrome 6 Crashing on Exit? Uninstall ViInputManager.
wordpress_id: 1798
categories:
- Technology
---

I was very excited to use Google Chrome 6, but the bummer was that it was crashing every time it exited. So it was not saving previous pages viewed, and generally was eating up my CPU doing the crash report. I finally took a detailed look at the crash report and noticed something about [ViInputManager](http://www.corsofamily.net/jcorso/vi/). This is a plug in that I had installed from Jason Corso's site. I really like the idea of being able to use Vi Keybindings in my Mac apps, but not if it makes my browser crash.

Here are his instructions for uninstalling, which should fix the crashing problem:





  1. 
Remove the directory (Tiger) ~/Library/InputManagers/ViInputManager or
(Leopard) /Library/InputManagers/ViInputManager.



  2. 
Remove the key binding. [I did not have to do this step, and couldn't find these files on my system - Ivan] If you have no other key bindings in your system, then simply remove the file:  ~/Library/KeyBindings/DefaultKeyBinding.dict.  Otherwise, in that file, remove the entries for "Vi_escapeMode".

