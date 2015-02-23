---
layout: post
title: VMware View optimization script breaks Windows security features
date: '2014-03-13 04:00:07'
---


![Attempt to access invalid address](/content/images/2014/12/Windows_7-1.png)

I've been using the [Windows Optimization Guide for View Desktops](http://www.vmware.com/resources/techresources/10157) guide on the VMware website for a long time. Hidden inside the PDF are some text file attachments that when converted to .bat, run though and disable most of the functions that bloat virtual desktop linked clones or are totally uncessary when accessed from a thin client or mobile device. However around October of last year during a customer engagement I noticed the PDF was updated with a revised version. That version has caused me a lot of headaches.

After running the revised scripts, I was basically left with broken templates. Internet Explorer would no longer load. Breaking Internet Explorer sort of makes me look like an idiot after I deploy entire pools of desktops and companies can't use them to run their corporate webapps.

I'd never got around to figuring out exactly what caused this issue, and because of it I'd been using a modified version of an older script during my engagements. However during a View implementation this week I was unable to find this older copy and so I decided I was going to figure out what made this new script such a pain.

###ASLR

> Address space layout randomization (ASLR) is a computer security technique involved in protection from buffer overflow attacks. In order to prevent an attacker from reliably jumping to a particular exploited function in memory (for example), ASLR involves randomly arranging the positions of key data areas of a program, including the base of the executable and the positions of the stack, heap, and libraries, in a process's address space. ([Wikipedia](http://en.wikipedia.org/wiki/Address_space_layout_randomization))

ASLR was a feature added to Windows starting with Vista. It's present in Linux and Mac OS X as well. For reasons unknown, the VMware scripts disable ASLR. Specifically, it's done by this registry entry command:

    reg ADD "HKLM\System\CurrentControlSet\Control\Session Manager\Memory Management" /v MoveImages /t REG_DWORD /d 0x0 /f
   
Internet Explorer will not run with ASLR turned off. After further testing, neither will Adobe Reader. Two programs that are major targets for security exploits, refuse to run with ASLR turned off.

The "problem" with ASLR in a virtual environment is that it makes transparent memory page sharing less efficient. How much less? That's debatable and dependent on workload. It might gain a handful of extra virtual machines running on a host, and at the expense of a valuable security feature of the operating system.

For some reason, those who created the script at VMware have decided that they consider it best practice for it to be disabled.

Or do they?

I actually can't find anywhere else in the document that says that ASLR should be disabled. Even in the table that lists all the changes that are done by the script, it's not listed, yet under the "changes since last version" the command referenced above is listed. I also can't find anything else on VMware's site that says it should be disabled. Actually, I found information to the contrary.

Back in 2011, [a VMware blog entry by Eric Horschman](http://blogs.vmware.com/virtualreality/2011/02/hypervisor-memory-management-done-right.html) specifically called out this issue and clarified that it is not recommended to disable ASLR in a general sense.

The same is true from André Leibovici (previously an Architect in the Office of the CTO End User Computing at VMware, now with Nutanix, and someone I consider to be a virtual desktop expert) who on his site [myvirtualcloud.net](http://myvirtualcloud.net/?p=2545) back in 2011 had this to say about ASLR, specifically in VDI:

> Is it a good practice to disable ASLR? The short answer is No. Unless you are pushing very high levels of memory overcommit in a 32-bit desktop VDI environment, you have a lot more to lose than to gain from disabling ASLR. On 64-bit platforms the loss of opportunities to share pages is much less due to the large memory page nature.

So how did this get added to the standard optimization script? Given VMware's public position that runs contrary to this, I assume it's there by mistake. I actually notified VMware about the fact that the script was breaking Internet Explorer back in October but it apparently had never been isolated, or possibly never investigated.

(The revised scripts also previously contained a bunch of incorrect ' and " characters in it, that also caused running most of the commands in it to fail. This was corrected.)

Sadly, the reason why Eric and Andre even brought this up in 2011 was because of Microsoft. In a couple of Microsoft blog entries ([1](http://blogs.technet.com/b/virtualization/archive/2011/02/09/windows-7-and-windows-server-2008-r2-sp1-add-new-virtualization-innovations.aspx)/[2](http://blogs.technet.com/b/virtualization/archive/2011/02/15/vmware-aslr-follow-up-blog.aspx)) they started spreading some FUD by attempting to say that VMware was suggesting that customers disable ASLR.

The reality was it was an topic was addressed to say that yes, you can increase consolidation ratios by turing off ASLR, but at the expense of security. There was a bit of back and forth from some of the VMware folks suggesting that Microsoft's implementation of ASLR isn't even all that effective at mitigating malware infections. I won't get into that.

Regardless, it's a security feature of the operating system, and in the case of the applications referenced above, one that totally breaks functionality. Hopefully, VMware will correct this soon. In the mean time, I'll be commenting on this line on all future engagements.