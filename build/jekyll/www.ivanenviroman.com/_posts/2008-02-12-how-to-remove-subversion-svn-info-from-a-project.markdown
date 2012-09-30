---
comments: true
date: 2008-02-12 17:35:07
layout: post
slug: how-to-remove-subversion-svn-info-from-a-project
title: How to remove subversion (SVN) info from a project
wordpress_id: 120
categories:
- Web Design
tags:
- ruby
- subversion
- svn
- Web Design
---

Sometimes when I'm coding I need to remove all the subversion ([SVN](http://svnbook.red-bean.com/) - a source code version control program, which if you're a non-programmer, [you could also use](http://lifehacker.com/software/subversion/hack-attack-how-to-set-up-a-personal-home-subversion-server-188582.php) for any documents you want to version control) information from the project. Perhaps you've copied the code to another directory and want to start a new source repository, or have some other reason. I wrote a short ruby script to help called 'stripsvn' Here it is:



    
    
    <code>#!/usr/bin/env ruby
    # note above line may need to be changed on linux - use 'which ruby' to find path to ruby
    # by Ivan Storck 13 February 2008
    puts "The current directory is #{ENV["PWD"]}"
    puts "About to delete ALL subversion info from this directory and all directories below"
    print "WARNING - this is permanent! Type YES to continue:"
    confirm = gets
    if confirm == "YES\n" or confirm == nil
      puts `find . -name .svn -type d -print0 | xargs -0 rm -rf` 
      puts "Deleted all subversion info"
    else
      puts "Command aborted"
    end
    </code>
    




I put this in a file called stripsvn in a folder called bash_scripts (I know, it's not written in bash, it's in ruby) - that was in my path from the command line so I could just type `stripsvn` at the terminal and run the command. You could put it anywhere, but it's useful to have a folder that you put scripts you've wrote in, and have it included in your path. You might also have to `chmod 755 stripsvn` to make it executable. This short script is a good example of using mostly ruby to write a useful shell script and only use bash or what I'd call "unix" commands when you have to. It's all ruby except for the line with the find that actually does the deleting.



