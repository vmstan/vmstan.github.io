---
layout: post
title: Markdown Complete
date: '2013-05-17 17:00:00'
---

So I've completed the process of reformatting all the previous posts on the site to the new Markdown style. The heavy lifting was done by a Python script I found called [ExitWP](https://github.com/thomasf/exitwp). It takes the XML formatted data from a WordPress export, and reads through it all and converts all of the content to Markdown based files for each post, ready to be eaten by the Jekyll engine that is behind [Octopress](http://octopress.org).

It still required a little bit of tweaking of each post to make sure things like IMG and YouTube tags showed up correctly.

The irony of the whole thing, is that I've done this already. Originally the site was all greated using Markdown for Second Crack. [One of the first posts I made covered this whole process](http://vmstan.com/2012/12/10/adventures-in-markdown/):
> As I set out to start blogging again, I wanted to try something about new with the backend. Again, I’ve been doing this since before it was as simple as signing up for a Blogger account, but I didn’t want to just create another WordPress.org site like I’d done in times past. Anyone can do that. I wanted to at least do something a little different, to learn through the process. I investigated a few different options for a totally Markdown based website management experience. The two serious ones I landed on were Second Crack by Marco Arment and Octopress by Brandon Mathis.

The problem was that Second Crack was not reliable or particularly well supported by the community. This led to frustration for me when I couldn't even manage to post content to the site after something in the system broke and I couldn't figure out what it was. [This culminated in me moving the entire thing to WordPress a few months ago](http://vmstan.com/2013/02/25/keep-it-simple-stupid/):
>I’ve used Wordpress a lot in the past, but usually self-hosted. This time around I’m going to use Wordpress.com and let them handle everything. We’ll see how well it goes with me being stuck in their little box. I do like a little flexibility and customization. At least with this if I decide I need to break out, I can export the data and go. (Having to manually import all my previous blog data today was not fun. Thankfully the site is only a few months old.)

As I predicted, I ended up exporting the data and going.