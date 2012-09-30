---
comments: true
date: 2007-09-12 12:04:59
layout: post
slug: how-to-delete-all-those-session-files
title: How to delete all those session files
wordpress_id: 73
tags:
- technology
---

#### Or what to do when rm * says "argument list too long" error.




_Note this post marks the addition/resuming of geeky (mostly ruby) programming posts to the blog. I'l still have all the regular sustainable marketing and eco-geek content, and will be modifying my feeds so that you can decide which content you want to subscribe to. I tried running two blogs but it was too much work to decide which one to post in! For now, you can also use the menu items at the top of the page to sort by category_





Rails apps create session files that are stored in the `/tmp/sessions` folder. And this folder tends to fill up with old files if you leave it too long. You might get so many files in there that the `rm` command does not work anymore. 


    
    <code>
    [~/cadvbe/tmp/sessions]# rm *
    -jailshell: /bin/rm: Argument list too long
    [~/cadvbe/tmp/sessions]# ls -1 | wc -l
    144433
    [~/cadvbe/tmp/sessions]# find . -name 'ruby_sess*' | xargs rm
    [~/cadvbe/tmp/sessions]# ls
    ./  ../  .svn/  
    </code>





The command `ls -1 | wc -l` counts how many files were in the directory. Over 144 thousand! Instead, use `find . -name 'ruby_sess*' | xargs rm` to find all the session files and pipe them to the rm command one at a time. This works.





Thanks to [MoundAlexis.com](http://www.moundalexis.com/archives/000035.php) for the idea, and read more on ruby sessions and automatically deleting them with a cron job [here](http://snippets.scottwalter.com/posts/show/83)






Technorati Tags:
[rails](http://technorati.com/tag/rails), [rubyonrails](http://technorati.com/tag/rubyonrails), [rm](http://technorati.com/tag/rm), [linux](http://technorati.com/tag/linux), [sessions](http://technorati.com/tag/sessions)




