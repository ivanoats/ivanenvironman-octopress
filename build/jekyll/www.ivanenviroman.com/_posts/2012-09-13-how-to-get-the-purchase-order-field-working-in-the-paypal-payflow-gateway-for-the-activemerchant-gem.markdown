---
comments: true
date: 2012-09-13 15:53:00
layout: post
slug: how-to-get-the-purchase-order-field-working-in-the-paypal-payflow-gateway-for-the-activemerchant-gem
title: How to Get the Purchase Order Field Working in the PayPal Payflow Gateway for
  the ActiveMerchant gem
wordpress_id: 2905
categories:
- UW Blog
---

This is pretty obscure, but if you need to fill out the PONUM (Purchase
Order) field while communicating with the PayPal Payflow gateway, here's
how to ensure the info gets transmitted to PayPal. It's not well
documented in either the PayPal or ActiveMerchant documentation.





I'm using the ruby gem [ActiveMerchant](http://activemerchant.org/) and
the [PayPal Payflow
Gateway](http://rdoc.info/github/Shopify/active_merchant/ActiveMerchant/Billing/PayflowGateway)





The PayFlow gateway has an instance method called
[authorize](http://rdoc.info/github/Shopify/active_merchant/ActiveMerchant/Billing/PayflowGateway#authorize-instance_method)



authorize method signature  
 
    
    <span class="line-number">1</span>
    <span class="line-number">2</span>
    <span class="line-number">3</span>
    <span class="line-number">4</span>
    <span class="line-number">5</span>
    <span class="line-number">6</span>
    <span class="line-number">7</span>
    <span class="line-number">8</span>
    
    
    <code class="ruby"><span class="line"><span class="c1"># File 'lib/active_merchant/billing/gateways/payflow.rb', line 16</span>
    </span><span class="line">
    </span><span class="line"><span class="k">def</span> <span class="nf">authorize</span><span class="p">(</span><span class="n">money</span><span class="p">,</span> <span class="n">credit_card_or_reference</span><span class="p">,</span> <span class="n">options</span> <span class="o">=</span> <span class="p">{})</span>
    </span><span class="line">  <span class="n">request</span> <span class="o">=</span> <span class="n">build_sale_or_authorization_request</span><span class="p">(</span><span class="ss">:authorization</span><span class="p">,</span> <span class="n">money</span><span class="p">,</span>
    </span><span class="line"><span class="n">credit_card_or_reference</span><span class="p">,</span> <span class="n">options</span><span class="p">)</span>
    </span><span class="line">
    </span><span class="line">  <span class="n">commit</span><span class="p">(</span><span class="n">request</span><span class="p">,</span> <span class="n">options</span><span class="p">)</span>
    </span><span class="line"><span class="k">end</span>
    </span></code>






You put your PO Number in the options hash, like this:



calling authorize  
 
    
    <span class="line-number">1</span>
    <span class="line-number">2</span>
    <span class="line-number">3</span>
    <span class="line-number">4</span>
    <span class="line-number">5</span>
    <span class="line-number">6</span>
    
    
    <code class="ruby"><span class="line"><span class="n">options</span> <span class="o">=</span> <span class="p">{</span>
    </span><span class="line">  <span class="n">billing_address</span><span class="p">:</span> <span class="n">address</span><span class="p">,</span>
    </span><span class="line">  <span class="n">comment</span><span class="p">:</span> <span class="s2">"blah blah"</span><span class="p">,</span>
    </span><span class="line">  <span class="n">po_number</span><span class="p">:</span> <span class="s2">"any old string works"</span>
    </span><span class="line"><span class="p">}</span>
    </span><span class="line"><span class="n">authorization</span> <span class="o">=</span> <span class="n">your_gateway_object</span><span class="o">.</span><span class="n">authorize</span><span class="p">(</span> <span class="n">amount</span><span class="p">,</span> <span class="n">credit_card</span><span class="p">,</span> <span class="n">options</span><span class="p">)</span>
    </span></code>






Hope this helps you if you found this post! Let me know in the comments
if it did.



