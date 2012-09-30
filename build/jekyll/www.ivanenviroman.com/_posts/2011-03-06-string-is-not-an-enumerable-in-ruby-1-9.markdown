---
comments: true
date: 2011-03-06 14:12:50
layout: post
slug: string-is-not-an-enumerable-in-ruby-1-9
title: String is not an Enumerable in Ruby 1.9
wordpress_id: 2162
categories:
- rubyonrails
- sysadmin shell scripts and source control
tags:
- error
- ruby19
- rubyonrails
---

![NEW-ruby-logo.jpg](http://www.ivanenviroman.com/wp-content/uploads/2011/03/NEW-ruby-logo.jpg)I had written some [code to generate a random password](http://www.sustainablewebsites.com/article/random-password-generator), which was working fine in Ruby 1.8, but was giving me this error in 1.9:



    
    <code>
      <p>undefined method `any?' for "bad-seed":String (NoMethodError)</p>
    </code>




It turns out this was because the String class in Ruby 1.9 now is no longer an Enumerable, so the any? method does not exist (and is undefined). This is because Strings are now encoded.




> 
  
> 
> In the Ruby 1.9 realm of all encoded data, blessing one type of iteration just doesn't make sense.  

> 
> 





> 
  
> 
> -- from James Edward Gray II's excellent [article about Strings in Ruby 1.9](http://blog.grayproductions.net/articles/ruby_19s_string)
> 
> 





You now have to tell Ruby exactly **what** you want to iterate over in the String:



    
    <code>
    "foo\nbar".lines.any? { |e| e == "bar" } => true
    "foo\nbar".chars.any? { |e| e == "b" } => true
    "foo\nbar".bytes.any? { |e| e == 97 } => true
    97.chr=> "a"
    </code>




> 
  
> 
> -- from a post on [comp.lang.ruby](http://www.rhinocerus.net/forum/lang-ruby/436631-ruby-1-9-doesnt-hace-string-any.html)
> 
> 





If you want even more detail on the pros and cons of String encoding in Ruby, check out this [hacker news article](http://news.ycombinator.com/item?id=1162122).
