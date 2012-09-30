---
comments: true
date: 2008-10-01 22:21:58
layout: post
slug: 404-error-pages-in-rails
title: 404 error pages in Rails
wordpress_id: 172
categories:
- Web Design
tags:
- '404'
- rails
- ruby on rails
- rubyonrails
- Web Design
---

I'm always trying to encourage visitors to my website to find the right information. I'm also pretty lazy with typing and want to be able to just guess at URL's and see if they work.




The new website system for Sustainable Websites, built in Ruby on Rails, has articles (called posts in WordPress) and pages. I wanted the page not found (HTTP status 404) page to automatically direct them to the appropriate page, if it exists, or article, and if it doesn't exist, provide some suggested links and a search box (pre-filled with some keywords from the URL they tried).




The initial part of this was based on Recipe 7 (page 43) of:![](http://ecx.images-amazon.com/images/I/513getfsjBL._SL160_.jpg)["Advanced Rails Recipes: 84 New Ways to Build Stunning Rails Apps (Pragmatic Programmers)" (Mike Clark)](http://www.amazon.com/Advanced-Rails-Recipes-Pragmatic-Programmers/dp/0978739221%3FSubscriptionId%3D0PZ7TM66EXQCXFVTMTR2%26tag%3Dfindmassage-20%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3D0978739221)


  



The first part was setting up a default route in routes.rb:



    
    # 404 handler
    map.connect '*path', :controller => 'four_oh_fours'
    




then here's the 404 controller:



    
    
    class FourOhFoursController < ApplicationController
       def index
       #clean the slash out of request.path.
       cleaned_path = request.path.gsub(/\//," ").strip
       #if request.path is in the set of page permalinks then redirect to that page
       to_page = Page.find_by_permalink(cleaned_path)
       if to_page then
         redirect_to page_permalink_url(to_page.permalink) and return false
       end
       #same if it is an article name
       to_article = Article.find_by_permalink(cleaned_path)
       if to_article then
         redirect_to permalink_url(to_article.permalink) and return false
       end
    
       #TODO: same if it a username?
    
       FourOhFour.add_request(request.host, request.path, request.env['HTTP_REFERER'] || '')
       respond_to do |format|
         format.html { render :file => "#{RAILS_ROOT}/public/404.html", :status => "404 Not Found" }
         format.all { render :nothing => true, :status => "404 Not Found" }
       end
       end
    end
    




It uses the Page model's find_by_permalink method but I could have easily just used find by title or another attribute of Pages.



