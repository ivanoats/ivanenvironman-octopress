---
comments: true
date: 2008-03-30 16:51:52
layout: post
slug: getting-down-to-coding-faster
title: Getting down to coding faster
wordpress_id: 139
categories:
- Web Design
tags:
- ruby on rails
- rubyonrails
- Web Design
---

When I reboot my mac, or need to switch projects, I had quite a few clicks and mouse movements to go through. I found it rather repetitive, so I set up a shell script (in ruby) to open Firefox, Textmate, and start the rails server.




Here's the script. I called it open_dev_environement and used `chmod 755 open_dev_environment` to make it clickable and executable from the project directory.



    
    
    <code># make sure your path to ruby is the same as above by typing 'which ruby' at the command line
    app_directory_name = "persfin"
    
    # start mongrel, using -c to change the directory 
    system 'mongrel_rails mongrel::start -c ~/Sites/' + app_directory_name + '&'
    
    # change Minefield to Firefox if you're not using the latest Firefox Nightly Beta
    `open -a /Applications/Minefield.app http://localhost:3000`
    
    # make sure your textmate project file has the same name as the directory
    system 'open -a TextMate ~/Sites/' + app_directory_name + "/" + app_directory_name + ".tmproj"
    </code>
    




It would be interesting to know how to extend this to open up multiple tabs in Terminal (for example, 'script/console') Or, if there is a better way to do these commands with osascript for applescript. If you know, let us all know in the comments.  
[see also Ruby may replace Applescript.](http://www.rubyinside.com/ruby-as-an-applescript-replacement-811.html)



