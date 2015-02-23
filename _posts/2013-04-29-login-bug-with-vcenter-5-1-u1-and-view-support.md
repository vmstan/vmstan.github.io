---
layout: post
title: Login bug with vCenter 5.1 U1, and View support
date: '2013-04-29 17:00:00'
---

A couple of important notices in regards to the recently released vCenter 5.1 U1. Take note before starting any upgrades.

  1. There has been a rather frustrating bug that has been discovered with vCenter 5.1 U1 when using Active Directory logins for administration. If you use a separate administrator account from your daily user account, you may be unable to login to the vCenter web or desktop clients if your user account is a member of more 19 or more Active Directory groups. ([Detailed in VMware KB 2050941](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2050941))
  2. <del>No version of VMware (Horizon) View has yet been certified with 5.1 U1. Currently only View 5.1 and 5.2 are certified with 5.1 pre-U1.</del>
  
**Update:** In the time I looked at the compatibility matrix, wrote this up and posted it, and just a few minutes ago when I was on the matrix again, it appears U1 is now listed as supported. Enjoy!
