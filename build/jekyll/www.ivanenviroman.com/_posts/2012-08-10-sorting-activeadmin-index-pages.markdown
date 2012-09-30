---
comments: true
date: 2012-08-10 12:57:00
layout: post
slug: sorting-activeadmin-index-pages
title: Sorting ActiveAdmin Index Pages
wordpress_id: 2824
categories:
- UW Blog
---

Here's how I got my list of
[Philosoraptors](http://knowyourmeme.com/memes/philosoraptor) sorted in a
[Ruby on Rails](http://rubyonrails.com) [ActiveAdmin](http://activeadmin.info)
app:



sort on a column called name  
 
    
    <span class="line-number">1</span>
    <span class="line-number">2</span>
    <span class="line-number">3</span>
    <span class="line-number">4</span>
    <span class="line-number">5</span>
    <span class="line-number">6</span>
    <span class="line-number">7</span>
    <span class="line-number">8</span>
    
    
    <code class="ruby"><span class="line"><span class="no">ActiveAdmin</span><span class="o">.</span><span class="n">register</span> <span class="no">Philosoraptor</span> <span class="k">do</span>
    </span><span class="line">  <span class="n">controller</span> <span class="k">do</span>
    </span><span class="line">    <span class="k">def</span> <span class="nf">index</span>
    </span><span class="line">      <span class="n">params</span><span class="o">[</span><span class="ss">:order</span><span class="o">]</span> <span class="o">=</span> <span class="s2">"name_asc"</span>
    </span><span class="line">      <span class="k">super</span>
    </span><span class="line">    <span class="k">end</span>
    </span><span class="line">  <span class="k">end</span>
    </span><span class="line"><span class="k">end</span>
    </span></code>






Because each Resource in ActiveAdmin (meaning table in the database,
or rails model) has a controller, you can
[modify the controller](http://activeadmin.info/docs/8-custom-actions.html#modify_the_controller).
What I did above was just add to the params array a key called `order` with
a value of `name_asc` - meaning I wanted my philosoraptors to be sorted in
order to by name, ascending (from a to z).





You can find out these order key values by looking at the end of
the URL in your browser, in Active Admin. The query string will be everything
after the ? in the URL, after clicking on one of the column names in the top row
of the table.





In my code example above, I put in the order parameter, then I called
`super` on the method to inherit the rest of the controller code from
ActiveAdmin.





Hopefully you find that this works for you. It's a pretty easy way of setting
up a default sort in ActiveAdmin. Let me know if you have any comments or troubles
getting it working in your app.



