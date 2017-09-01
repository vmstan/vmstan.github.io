---
layout: post
title: July 2014, on Twitter
date: 2014-07-03 17:37
author: marshalus
comments: true
categories: [Social Media, Twitter, Uncategorized]
---

I’ve been trying to determine the best way to link the blog and my Twitter account together. Obviously I tweet links to much of what I post here, but I tweet far more often than I blog. There are usually lots of good nuggets that I find, either links to other blogs, KB articles, or even just retweeting insights.

As an experiment I’m going to start putting together a little digest with some extended comments from me on them. Sometimes they’re the most popular things I’ve shared, sometimes the things I’ve found the most interesting, or sometimes just my failed attempt at being funny. So here we go.

> _Storage Controllers previously supported for VSAN that are no longer supported_ [_http://t.co/XQTXJscMUr_](http://t.co/XQTXJscMUr)

> _— Michael Stanclift (@vmstan)_ [_July 2, 2014_](https://twitter.com/vmstan/statuses/484308107506376704)

Take note of the Dell PERC H310\. This is in no doubt response to the VSAN Day from Hell that one unlucky user experianced a few weeks ago. The low queue depth on these cards prevent VSAN from performing as it should. It was good of VMware to yank these to prevent further issues, but frustrating that it wasn’t accounted for prior to rollout.

> _“I try not to be a bad mom” says_ [_@SadieStan_](https://twitter.com/SadieStan) _“Try try try, and you’ll get better” replies_ [_@PDanStan_](https://twitter.com/PDanStan)[_#smartass2yo_](https://twitter.com/hashtag/smartass2yo?src=hash)

> _— Michael Stanclift (@vmstan)_ [_July 1, 2014_](https://twitter.com/vmstan/statuses/483794848298704896)

Kids say the darndest things.

> _Just sat for the VCAP-DTA exam. Feeling pretty good, which probably means I failed. Guess I know soon enough._

> _— Michael Stanclift (@vmstan)_ [_June 30, 2014_](https://twitter.com/vmstan/statuses/483655866076233729)

I failed. Second attempt is August 2.

> _This kid got up at 8am asking to go to the Apple Store. Dad makes dreams come true._ [_pic.twitter.com/fs2MjF8nS9_](http://t.co/fs2MjF8nS9)

> _— Michael Stanclift (@vmstan)_ [_June 29, 2014_](https://twitter.com/vmstan/statuses/483046250829193216)

I do what I can to raise my children right.

> _Testing out Zentyal as a new home domain controller. I like what I’ve seen so far._

> _— Michael Stanclift (@vmstan)_ [_June 28, 2014_](https://twitter.com/vmstan/statuses/483010187817533440)

It’s actually worked out really well, so far. I need to get into setting up LDAP and vCenter authentication for it. One less reason to have anything Windows running in the home. I also switched the home firewall from Untangle over to pfSense. This will change again soon once I get my Cisco Meraki firewall, switch and access point for the house. (Doing partner level CMNA training this Wednesday.)

> _Facebook manipulated for a massive psych experiment_ [_http://t.co/x4IPrxqSYR_](http://t.co/x4IPrxqSYR)_ … remember when it just showed you what your friends were up to?_

> _— Michael Stanclift (@vmstan)_ [_June 28, 2014_](https://twitter.com/vmstan/statuses/482739865876828160)

This shit still has me pissed off, and logged off of Facebook on most of my devices.

> _Google encrypting data in transit and at rest to Drive is great and all, but who has the keys? If Google, then what difference does it make?_

> _— Michael Stanclift (@vmstan)_ [_June 26, 2014_](https://twitter.com/vmstan/statuses/481988890455068672)

Any encryption is good, but I’m not exactly jumping up and down with excitement about it.

> _I completely bricked a fabric interconnect during a code upgrade today. Achievement unlocked._

> _— Michael Stanclift (@vmstan)_ [_June 25, 2014_](https://twitter.com/vmstan/statuses/481939830020927488)

Last but not least, what a mess this upgrade was. I won’t get into details since it involves a customer environment, but it was a stressful couple of days when we discovered Smartnet didn’t get renewed on their UCS environment as expected, after the FI was totally bricked. Our company was able to get it resolved with Cisco and they had a new one in the rack and running less than 24 hours later, still not fun.