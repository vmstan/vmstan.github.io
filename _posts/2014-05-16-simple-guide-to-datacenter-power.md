---
layout: post
title: Simple guide to datacenter power
date: 2014-05-16 04:08
external_url: http://www.jpaul.me/?p=7672
host: Justin Paul's Blog
---

> Power… it is the only thing that you will find more prevalent in a datacenter than racks, yet many times when discussing upgrades and new installations it’s the part that no one ever mentions.
> - the IT team isn’t in charge of the power design (leased building, union, or separate electrical department)
> - have always just used 120v “normal” stuff under 1800 watts
> - aren’t an electric engineer/don’t understand what Amps, Volts, Watts are
> - don’t understand all of the options for connectors/cords

I’m guilty of these things, especially when I was just an administrator. Since becoming a consultant I’ve had to take a crash course (heh) in things like the differences between an C13 and an NEMA 5–15, 120 vs 208, etc.

Power always seems to be a major issue on projects these days, especially as more and more customers adopt blade systems like the Cisco UCS. What has really been difficult has been the latest generation of EMC VNX now requires 208v power on the Disk Processor Enclosure (there is a block only 5200 model that can run on 120, but you have to order it ahead of time, it doesn’t autoswitch by default anymore.)

Better understanding by customers is essential.
