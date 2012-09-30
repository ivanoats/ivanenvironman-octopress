---
comments: true
date: 2008-02-20 08:50:10
layout: post
slug: rake-tasks-for-dumping-mysql
title: Rake Tasks for dumping mysql
wordpress_id: 123
categories:
- Web Design
tags:
- mysql
- rake
- ruby on rails
- rubyonrails
- sake
- Web Design
---

I have definitely used [sqlite](http://solutions.treypiepmeier.com/2006/10/22/using-sqlite-with-rails/) database files but I also like sticking to [mysql](http://hivelogic.com/articles/installing-mysql-on-mac-os-x/), because I know that's what I'll use on the the server. I've created some rake tasks to help me in this process. As usual, they go in `lib/tasks`.




here's my `db.rake` file:



    
    
    <code>
    # with thanks to sake
    # http://errtheblog.com/posts/60-sake-bomb
    namespace :db do
    
      # command line usage: rake db:version
      desc "Returns the current schema version"
      task :version => :environment do
        puts "Current version: " +
          ActiveRecord::Migrator.current_version.to_s
      end
      
      #rake db:dump
      desc "dumps the devel database to a sql file" 
      task :dump => :environment do   
        puts "Creating .sql dump file. Enter mysql root password. Just press Enter for none"
        #run a shell command mysqldump -u user -p database name to file name
        `mysqldump -uroot -p app_development > app_development_dump.sql`
      end
      
      #command line usage: rake db:dumpimport
      desc "imports the devel databse dump file to www2_sw"
      task :dumpimport => :environment do
        puts "Loading www2_sw_development_dump.sql. Enter mysql root password. Just press Enter for none"
        `mysql -uroot -p app_development < app_development_dump.sql`
      end
      
    end
    </code>
    




Note you might want to use another mysql user to access your database. For example, `-u yourusername`. I like doing this so I can check in the dump file into subversion or whatever version control system you're using. If you find this incredibly useful, you may want to [sake](http://errtheblog.com/posts/60-sake-bomb) bomb it, which would make it available to all your projects. Bonus points for commenting on how to do this below (please?) It would also be cool to automatically grab the production database name.



