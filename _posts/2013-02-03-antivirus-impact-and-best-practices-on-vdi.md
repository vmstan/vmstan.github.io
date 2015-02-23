---
layout: post
title: Antivirus impact and best practices on VDI
date: '2013-02-03 18:00:00'
---

Project VRC (virtual reality check) has [an excellent white paper](http://www.projectvrc.com/white-papers) on antivirus in virtual desktops. I started writing about this a few weeks ago, but I was having issues with Dropbox sync on my server so the file got lost in the Ether.

The big takeaway for me was to run full virus scans on the gold image before deployment. That is something I never considered doing before. I still think deploying something like Deep Security or another vShield Endpoint, hypervisor based, scanning tool is the best route. (Especially now that it’s free with 5.x licensing.)
