---
layout: post
title: View optimization guide updated to correct ASLR issue
date: '2014-07-21 19:32:42'
---

A few months ago [I wrote about](http://vmstan.com/view-optimization-script-breaks-windows-security-features/) the VMware View optimization script breaking Internet Explorer and Adobe Acrobat through the addition of a registry entry that disabled Address Space Layout Randomization (ASLR):

> ASLR was a feature added to Windows starting with Vista. It's present in Linux and Mac OS X as well. For reasons unknown, the VMware scripts disable ASLR. 

> Internet Explorer will not run with ASLR turned off. After further testing, neither will Adobe Reader. Two programs that are major targets for security exploits, refuse to run with ASLR turned off.

>The "problem" with ASLR in a virtual environment is that it makes transparent memory page sharing less efficient. How much less? That's debatable and dependent on workload. It might gain a handful of extra virtual machines running on a host, and at the expense of a valuable security feature of the operating system.

> For some reason, those who created the script at VMware have decided that they consider it best practice for it to be disabled.

At the [VMware Partner Technical Advisory Board on EUC](http://vmstan.com/ptab/) last month, I pointed this out to some VMware people and sent a link to the blog entry. 

Over the weekend I got a tip from Thomas Brown from over at Varrow:

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/vmstan">@vmstan</a> looks like they updated the windows optimization guide for view. I assume they incorporated your changes into the script?</p>&mdash; Thomas Brown (@thombrown) <a href="https://twitter.com/thombrown/statuses/490559188355923968">July 19, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Today I had an opportunity to download the updated scripts ([available here](http://www.vmware.com/resources/techresources/10157)) and was very pleased to see:

	rem *** Removed due to issues with IE10, IE11 and Adobe Acrobat 03Jun2014
	rem Disable Address space layout randomization
	rem reg ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" /v MoveImages /t REG_DWORD /d 0x0 /f
	
Success!

As always, please review the rest of the contents to make sure the changes that the script makes are approprate for your environment.