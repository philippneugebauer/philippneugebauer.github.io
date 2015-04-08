---
layout: post
title: Automated Post File Generation
date: 2015-04-08 19:59:56 +0200
categories: Jekyll Automation Post File Generation
---

All the time, I was really annoyed about the blog post creation in Jekyll when I needed to create a new file
and then to rename it to `day-title.markdown`. Today, I just searched for a better solution and found this 
[great approach](http://arjanvandergaag.nl/blog/creating-new-jekyll-posts.html)
which I slightly adapted to my needs.

Because I'm not satisfied by the syntax of the post generation through the parameter passing with Rake, 
I will do in the future further investigation to solve it. For now, it's fine and better than to create post files manually.
Actually, the rewriting research wasn't easy because the syntax of Rake changed probably somewhen in 2012 
which made it really hard to find actual solutions to the problem.

The other possible solution compared to the environment variable passing would be: 

	task :post, [:title] do |task, args|
  		title = args.title

It is then called with `rake post["Title"]`. Compared to the to the environment variable solution much uglier it is much uglier as you can see:

	task :post do
		title = ENV['title']

That is simple called with `rake post title='your_title'` which is much more beautiful.
