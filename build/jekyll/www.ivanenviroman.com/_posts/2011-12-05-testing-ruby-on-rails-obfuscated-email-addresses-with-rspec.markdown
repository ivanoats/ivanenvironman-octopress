---
comments: true
date: 2011-12-05 16:26:00
layout: post
slug: testing-ruby-on-rails-obfuscated-email-addresses-with-rspec
title: Testing Ruby on Rails Obfuscated Email Addresses with RSpec
wordpress_id: 2548
categories:
- UW Blog
---

![](http://staff.washington.edu/ivanoats/images/nospam.jpg) You may have known that Ruby on Rails can protect email addresses that you have on your web pages with the [mail_to](http://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-mail_to) view helper. But how do you test email obfuscation in your RSpec view tests?





To obfuscate an email address in a rails view, you can simply add encode: "javascript" to your mail_to helper.



obfuscate and protect an email address  
 
    
    <span class="line-number">1</span>
    
    
    <code class="ruby"><span class="line"><span class="n">mail_to</span> <span class="s2">"you@example.com"</span><span class="p">,</span><span class="s2">"email me"</span><span class="p">,</span> <span class="n">encode</span><span class="p">:</span> <span class="s2">"javascript"</span>
    </span></code>






To test this, I created a method in my spec/spec_helper.rb file. This method goes through each character (byte) of the string containing the email address, and calls the [sprintf](http://apidock.com/ruby/Kernel/sprintf) method to format the character in the way that the javascript decoder in rails can read.



email encoder to include in spec_helper.rb  
 
    
    <span class="line-number">1</span>
    <span class="line-number">2</span>
    <span class="line-number">3</span>
    <span class="line-number">4</span>
    <span class="line-number">5</span>
    <span class="line-number">6</span>
    <span class="line-number">7</span>
    
    
    <code class="ruby"><span class="line">  <span class="k">def</span> <span class="nf">encode_email</span><span class="p">(</span><span class="n">email</span><span class="p">)</span>
    </span><span class="line">      <span class="c1"># copied escape method from:</span>
    </span><span class="line">      <span class="c1">#http://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-mail_to</span>
    </span><span class="line">    <span class="n">escaped</span> <span class="o">=</span> <span class="s2">""</span>
    </span><span class="line">    <span class="n">email</span><span class="o">.</span><span class="n">each_byte</span> <span class="p">{</span> <span class="o">|</span><span class="n">c</span><span class="o">|</span> <span class="n">escaped</span> <span class="o"><<</span> <span class="nb">sprintf</span><span class="p">(</span><span class="s2">"%%%x"</span><span class="p">,</span><span class="n">c</span><span class="p">)</span> <span class="p">}</span>
    </span><span class="line">    <span class="k">return</span> <span class="n">escaped</span>
    </span><span class="line">  <span class="k">end</span>
    </span></code>






Having that method available makes my example very easy to read:



email encoding example  
 
    
    <span class="line-number">1</span>
    <span class="line-number">2</span>
    <span class="line-number">3</span>
    
    
    <code class="ruby"><span class="line"><span class="n">it</span> <span class="s2">"should obfuscate and display the contact email"</span> <span class="k">do</span>
    </span><span class="line">  <span class="n">render</span><span class="o">.</span><span class="n">should</span> <span class="n">have_content</span><span class="p">(</span><span class="n">encode_email</span><span class="p">(</span><span class="s2">"contact@example.com"</span><span class="p">))</span>
    </span><span class="line"><span class="k">end</span>
    </span></code>






Do you know a better way? For example, hooking directly into the view helper code from [ActionView::Helpers::UrlHelper#mail_to](http://api.rubyonrails.org/classes/ActionView/Helpers/UrlHelper.html#method-i-mail_to)? Let me know in the comments.



