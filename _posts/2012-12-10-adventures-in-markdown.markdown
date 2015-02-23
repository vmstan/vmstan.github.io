---
layout: post
title: Adventures in Markdown
date: '2012-12-10 18:00:00'
---

Those who know me and see this website probably think, "oh man, another blog."

I've been doing this blogging thing off and on, since before anyone other than us nerds knew what the purpose of the Internet was. (Well, the one besides porn.) Each time I've had high hopes and lost steam by over extending myself. In the past I've started out with the purpose of becoming (more) Internet famous, and realized that it's much harder then it is made to seem. I've had my own sites for years, then worked for larger sites, then tried to start and fail and start and fail. My problem was I'd never really just done a site for me. So that's what this is. It's me in 2012, going into 2013, and beyond. Where it goes from there is just what I put into it, and not being driven by Klout scores or advertising revenue.

The primary purpose of this adventure is to have a place of my own to share my knowledge and experiences with virtualization and storage technologies, which is what I get paid during the times I'm not chasing my son around the house, to implement for customers around Kansas City, and enjoy doing. This includes providing links to helpful or interesting resources for virtualization/storage administrators and consultants, among other professional geek things. (Note: I’m an Apple gear-head, so probably lots of that coming here too.) Again, this is a site for me, but that I hope you'll enjoy reading.

Another purpose was to get back in the web publishing game and learn how all the cool bloggers are doing things in 2013.

Sure there are the basics like HTML5 and CSS that I’m going to have to get a grip on, and I've neglected to advance my skills on since the early 2000s (after I went to go write for Neowin and had other people on their team managed those things.) But as someone who is always interested in new ways of doing things there was more to it than just web programming.

For the last year or two, I kept seeing all these reviews on Apple sites I frequent for OS X and iOS text editing apps that support “Markdown” ... and just kind of ignored them because I’m not a programmer or a hacker.

Then one day I decided that I’d run a quick Bing Search (I'm joking no one uses that shit) and actually find out what Markdown was all about. What I saw I found interesting.

Created by Apple tech blogger and developer John Gruber, Markdown is just a simple way to create web documents. Instead of using ugly WYSIWYG inputs, which often results in nasty code and not really pretty results for perfectionists like me, or writing everything in plain text and manually adding complex HTML tags to match the desired output format, Markdown lets you use a basic method of encoding that can then be translated by an interpreter into HTML, for use on a website. In my mind its something between the two extremes.

As I find with most things in the Apple ecosystem, it’s simple, elegant and (somewhat) easy to learn. As
[John Gruber explains](http://daringfireball.net/projects/markdown/syntax) on his site:


> Markdown is intended to be as easy-to-read and easy-to-write as is feasible.

Readability, however, is emphasized above all else. A Markdown-formatted document should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions. While Markdown’s syntax has been influenced by several existing text-to-HTML filters — including Setext, atx, Textile, reStructuredText, Grutatext, and EtText — the single biggest source of inspiration for Markdown’s syntax is the format of plain text email.

To this end, Markdown’s syntax is comprised entirely of punctuation characters, which punctuation characters have been carefully chosen so as to look like what they mean. E.g., asterisks around a word actually look like _emphasis_. Markdown lists look like, well, lists. Even blockquotes look like quoted passages of text, assuming you’ve ever used email.


Readability kind of struck me, and stuck with me.

One of my goals, with this site, is to bring some of the simplicity of the Fireballed format to the virtualization community. A place for reader to land and get important bits of information in a clean and readable format. I'm not an incredibly smart person, so I will let incredibly smart people like [Simon Long](http://www.simonlong.co.uk/blog/), [Duncan Epping](http://www.yellow-bricks.com/) and [Scott Lowe](http://blog.scottlowe.org/) do the heavy lifting, so we can both benefit) and direct you there where appropriate. My opinion and experience, as limited as it is by comparison, can be thrown in for good measure.

As I set out to start blogging again, I wanted to try something about new with the backend. Again, I've been doing this since before it was as simple as signing up for a Blogger account, but I didn’t want to just create another WordPress.org site like I’d done in times past. Anyone can do that. I wanted to at least do something a little different, to learn through the process. I investigated a few different options for a totally Markdown based website management experience. The two serious ones I landed on were [Second Crack](https://github.com/marcoarment/secondcrack) by Marco Arment and [Octopress](http://octopress.org) by Brandon Mathis.

Initially I’d thought Octopress would be what I’d use because it came a little more feature rich and polished out of the box, but after trying to wrap my head around the Ruby frameworks required to make Octopress work, I realized that Second Crack was probably a better choice.

The thing that I found appealing about both systems is that all of the content for the site is static HTML files. No content is dynamically generated when a user visits the site using PHP or ASP files with a backend MySQL or MSSQL database, like what you'd see with WordPress, Drupal, or other systems. Just flat, simple, low-overhead HTML files. (Automagically generated when new content is loaded.)

I was already familiar with PHP, which is what Second Crack uses to generate the HTML files in the backend, so that made it a less abrasive choice for customization. The thing I really find neat about Second Crack is that it uses Dropbox to do most of the daily site management. The processes running on the web server monitor a Dropbox enabled folder for new content to post. New posts are created and saved in simple text files using Markdown format with the .md file extention.

As a result, I can drop them into a shared Dropbox folder on my laptop, iPad or other device, and within seconds they’re on my server where the Second Crack engine converts them to HTML and posts them to the website. Round trip the .md file on my laptop makes its way into published content in just a few seconds. The .md file is then later editable inside my Dropbox folder and upon save is resynced to the published content on my website. Draft pages can be saved, and an HTML file generated and placed in another Dropbox accessable folder on my laptop, so I can see exactly what the published content will look like without effecting the live site.

Saving the content on Dropbox also makes the revision history accessable, so if I acceidently delete a draft, or make changes I want to undo, I can easily roll back content through Dropbox.com. The locally saved .md files are also backed up to my Time Machine NAS and off-site to Backblaze so the content exists in multiple places. In contrast, and against my own self professed backup obsession, most of the time when I manage websites with MySQL databases, I fall into the trap of not backing up the database on a regular basis. If/when the database corrupts, or I make undesired changes, it’s a lot harder then fixing a corrupt .md or .html file by restoring a couple of 4k text files.

Second Crack’s simplicity and ease of backup, plus the ability to make changes or publish content on my website anywhere I can get access to those .md files (which when using an editor like Bywords, is just about anywhere) made it very attractive for me.

I like the fact that my content at its core is basically all plain text. It makes things a little more future proof should Second Crack not be everything it's cracked up to be. I’ve been swimming in the database driven content world for a while, and I have to say this refresh of doing things the old feels just so much cleaner. Time will tell if that remains to be the case. At the very least, not having the processor overhead of dynamically generated content and databases means a less powerful VM and less money required to finance operations of the website.

Which reminds me, after evaluating a few options for virtual server hosting, I finally landed on Rackspace Cloud to host this website. It's running out of their "next-generation" environment in Chicago, and I've been very impressed. The management interface is very nice, clean and easy to reimage the VM (which I did a few times in the process of getting things setup.) It's a 512MB virtual machine running CentOS 6.3.

It kills me that it's not on a VMware based virtual server, but, someday.

My hope is that the low footprint site and the reliable infrastrucutre that can be scaled up as needed can host this site even under heavy traffic load.

So bring on the visitors.
