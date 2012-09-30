---
comments: true
date: 2011-02-18 17:37:27
layout: post
slug: how-to-host-your-website-for-15-cents-a-month
title: How to Host Your Website for 15 Cents a Month — Creating Your First Website
  on Amazon S3
wordpress_id: 2095
categories:
- Web Design
tags:
- amazon
- hosting
- s3
- tutorial
---





		


		

This post will show you step-by-step how to create a website on the Amazon S3 service. Amazon Simple Storage Service (S3) is a cloud system that offers very low prices for file storage and now serves web pages, too.






A disadvantage is that you cannot run popular PHP programs like WordPress, Drupal or Joomla on it. However, it is a good low cost solution for HTML/CSS only (static) websites. Costs are around 15 cents per GB of storage, which is much cheaper than even the cheapest full-featured web host.






BTW, If you want to host a website that has more interactivity, like a [WordPress](http://www.sustainablewebsites.com/wordpress-hosting) or other PHP or Ruby on Rails based site, I run a [green web hosting](http://www.sustainablewebsites.com) company called [SustainableWebsites.com](http://www.sustainablewebsites.com). You'll probably want a real hosting plan if you want more features, or email at your domain name, too (although you could get a free Google Apps plan for that). 

	
	


	
		


	        

### Log in to Amazon Web Services


		


	![media_1298054884799.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298054884799.png)



	

1. Go to:  

[http://aws.amazon.com/console](http://aws.amazon.com/console)  

2. Find  "Sign in to the AWS Console"  - the big yellow-orange button on the right.  

3. Make sure Amazon S3 is selected in the drop down  

4. Click on the sign-in button.





	


	


	        

### Sign in with your Amazon ID


		


	![media_1298054995946.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298054995946.png)



	

Sign in with your existing amazon credentials or create a new user





	


	


	        

### Create a bucket for your website


		


	![media_1298055073314.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298055073314.png)



	

1. Click the Create Bucket button on the left





	


	


	        

### Name your bucket


		


	![media_1298077513961.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298077513961.png)



	

Choose a name for your bucket and select a region, then press create. Make sure the name for your bucket matches the domain name of your site and begins with "www."





	


	


	        

### Configure your bucket properties for hosting a website


		


	![media_1298055558480.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298055558480.png)



	

1. Click on the  bucket "Properties" button. It has a blue circle with a white i in the objects and folders section  

2. Click on the "Website" tab in the properties section below  

3. Check off Enabled  

4. Name your index document, which is your home page. Most commonly, index.html  

5 (optional). Name your error document. I chose 400.html but you could also do 404.html. This document will be displayed for any 400 errors  

6. Click the "Save" button  

7. You should see a green checkmark flash after save. Don't worry if you don't it is easy to miss.  

8. Right click on the link where it says "Endpoint" and save it in your clipboard for later





	


	


	        

### Create a HTML file (Mac, Step 1)


		


	![media_1298065917651.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298065917651.png)



	

You can use any HTML editor or even Notepad (Windows) or TextEdit (mac) to create a HTML file.  If you need one to start off with, Include the following lines in the file:






If you're on a Mac using TextEdit, make sure to go to the Format menu and choose "Make Plain Text" first. (Apple-Shift-T)






<html>  

<head>  

<title>Hello World</title>  

</head>  

<body>  

<h1>Hello World</h1>  

</body>  

</html>





	


	


	        

### Save your HTML file (Mac, Step 2)


		


	![media_1298078956910.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298078956910.png)



	

1. Choose File, Save As...  

3. Change Untitled to index  

4. Make sure the hide extension checkbox is off  

5. Make sure the filename is index.html  

6. Click the "Save" button and note where you saved it (defaults to Documents)





	


	


	        

### Create a HTML file (Windows)


		


	![media_1298066303173.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066303173.png)



	

1. Click on the start menu  

2. Click on All Programs  

3. Click on Accessories  

4. Click on Notepad  

5. Paste in the HTML:






<html>  

<head>  

<title>Hello World</title>  

</head>  

<body>  

<h1>Hello World</h1>  

</body>  

</html>






6. Choose File, Save As...  

7. Name the file index.html  

8. Make sure the "Save as type" is "All Files"  

9. Save to your Documents





	


	


	        

### Test your HTML file locally


		


	![media_1298066510837.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066510837.png)



	

Double click the index.html file to open it in your default browser





	


	


	        

### Upload your HTML file to AWS


		


	![media_1298066665376.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066665376.png)



	

Click on the Upload button (in the Objects and Folders section)





	


	


	        

### Select the file from your local machine and then Start Upload


		


	![media_1298066766958.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066766958.png)



	

Click on the Start Upload button





	


	


	        

### See that the file has finished uploading


		


	![media_1298066789789.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066789789.png)



	


	


	        

### Make index.html public


		


	![media_1298066892294.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066892294.png)



	

1. Highlight the index.html file in the "Objects and Folders" section  

2. Choose "Make Public" from the Actions menu





	


	


	        

### Load up your website at your AWS URL


		


	![media_1298066996074.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298066996074.png)



	

If you need a reminder on how to get your unique URL, go back to step "Configure your bucket properties" or just click on the Properties button in the "Objects and Folders" section, then the Website Tab. Your "Endpoint" link is what you want to load up in your browser to test.





	


	


	        

### Set your DNS CNAME to point to your AWS URL


		


	![media_1298071911642.png](http://www.ivanenviroman.com/wp-content/uploads/2011/02/media_1298071911642.png)



	

This step has a lot of different options because every domain name registrar or control panel system is different. Basically, you need to set a CNAME record for your domain to point to your AWS URL (without the http://). Here's a shot of how you would do this at [SustainableDomains.com](http://sustainabledomains.com) .  You can also forward the A record (example.com, without the www) to your CNAME record (www.example.com) at most registrars. There is a more detailed article [here](http://carltonbale.com/how-to-alias-a-domain-name-or-sub-domain-to-amazon-s3).





	


	


	        

### Done! View your site in your browser


		 


	

You may need to wait for an hour or more for the domain name to start resolving to AWS depending on your DNS TTL values. 





	







