---
layout: post
title: Another day, another CMS
date: '2013-12-18 22:05:06'
---

I can't make up my mind when it comes to blogging engines. Honestly there are a lot of options out there, but I'm one of those people who just can't leave well enough alone. 

* December 2012: [vmstan.com launched using Second Crack](http://vmstan.com/adventures-in-markdown/)
* February 2013: [Site moved to WordPress.com](http://vmstan.com/keep-it-simple-stupid/)
* May 2013: [Site moved back to Jekyll based Octopress](http://vmstan.com/markdown-complete/)
* December 2013: Site moved to node.js based Ghost

You can look back if you want my rationale for each move. My current thinking though is that Octopress was too difficult to update regularly with. Both Second Crack and Octopress relied on me having access to my laptop to generate the static HTML files for the site. The harder it is to post, the less posting I did. Wordpress solved this problem but wasn't really all that sexy.

[Ghost](http://ghost.org) solves this issue by combining a server side GUI, slim node.js powered site generation with a MySQL backend, and the ability to write content using Markdown.

It's pretty feature limited at this point. Other than tagging, being able to manually set the date of posts, and saving drafts then publishing content, there isn't much to the backend. I actually kind of like it. The default template is pretty slim right now, it might be a motivation to take matters into my own hands and spice it up, but I may just leave that to the professionals.

The site itself is running on a Rackspace virtual machine, just like the Second Crack and Octopress versions were. (Ubuntu 12.04 LTS) This time I utilized the Rackspace Deployments option from within their Cloud Control Panel to automatically provision a VM with Ghost, node.js, MySQL and all the other required technologies already to go.

I'm looking forward to see where the development team with Ghost takes the product. It just went GA a couple of months ago, so it only has room to grow. Somewhere it was said it's what Wordpress would be if it were reinvented and released now. We'll see. I hope to not need to convert the site to some other backend in 6 months, but it wouldn't surprise me if I did.