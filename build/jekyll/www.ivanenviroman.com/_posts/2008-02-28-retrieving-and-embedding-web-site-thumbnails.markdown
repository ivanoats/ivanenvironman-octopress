---
comments: true
date: 2008-02-28 05:25:30
layout: post
slug: retrieving-and-embedding-web-site-thumbnails
title: Retrieving and Embedding Web Site Thumbnails
wordpress_id: 128
categories:
- Web Design
tags:
- picoshot
- thumbnails
- Web Design
- webdesign
---

![](http://image.picoshot.com/thumbnail.php?domain=www.ivanenviroman.com)The [Picoshot](http://picoshot.com/) service allows you to embed a thumbnail image of another website in your page with a simple <img> tag. And, I was also able to use curl on the command line to create a file.




A little HTML is all you need to know. There are currently 2 ways to retrieve a thumbnail:





  
  * `<img src="http://image.picoshot.com/thumbnail.php?url=http://www.example.com">`


  
  * `<img src="http://image.picoshot.com/thumbnail.php?domain=example.com">`




Just replace example.com with the domain you wish to get the thumbshot for. It's that simple to get a thumbnail for free. Currently only domain and sub domain front pages are available, with internal pages a coming feature.




For the command line, you must have curl installed, and then use something like this:



    
    
    <code>curl -o sw-thumb.jpg http://image.picoshot.com/thumbnail.php?domain=sustainablewebsites.com</code>
    




Notice the -o switch is lowercase, you might be used to using the -O uppercase version to automatically name the file. Sometimes it takes a couple of tries with curl if the thumbnail has not been generated already for the site. If you figure out how to do this in JavaScript, Ruby, or PHP please let us know in the comments!



