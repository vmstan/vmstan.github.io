---
layout: post
title: Snow Leopard lacks security features present in Windows Vista/7
date: 2009-09-17 00:00
---


Noted Apple security analyst Charlie Miller, author of _The Mac Hackers Handbook_ and two-time winner of the Pwn2Own hacking contest has said, in an interview with [TechWorld](http://news.techworld.com/security/3201863/snow-leopard-less-secure-than-windows-says-hacker/?pn=1), that the latest version of Apple OS X (10.6 AKA Snow Leopard) lacks full and proper implementation of memory address space layout randomization (ASLR). ALSR is a technology, present in Windows Vista and Windows 7, that randomly assigns data to memory to make it difficult for attackers to determine the address of critical operating system functions being stored in memory, and therefore making it harder for them to create exploits.

“It’s the exact same ASLR as in Leopard, which means it’s not very good,” Miller said, “Apple didn’t change anything. I don’t understand why they didn’t. But Apple missed an opportunity with Snow Leopard.”

When OS X 10.5 (Leopard) was released, Miller and others were critical of Apple not fully implementing ASLR. While there is ASLR present in both Leopard and Snow Leopard, they fail to the heap, the stack and the dynamic linker, the parts of the operating system that are most open to attack. Linux also has what many consider a weak implementation of ASLR since kernel version 2.6.12, although some distributions include better ASLR then the stock kernel based on third party code.

Miller did say that there are elements of Snow Leopard that show Apple did do some things to improve security, most notably the inclusion of data execution prevention or DEP, which utilizes both processor-hardware and software based security programming to help prevent buffer overflow attacks by blocking code from running in memory spaces that’s supposed to contain only data.

However, Apple may be late to the game with implementation of DEP, as it has been present in Windows operating systems since Windows XP Service Pack 2, with further refinements made in Windows Vista and Windows 7.

By incorporating both technologies, Miller says it becomes extremely difficult to craft memory attack exploits. “If you don’t have either, or just one of the two [ASLR or DEP], you can still exploit bugs, but with both, it’s much, much harder. Snow Leopard’s more secure than Leopard, but it’s not as secure as Vista or Windows 7.”

* * *

_Originally published at_ [_techvirtuoso.com_](http://techvirtuoso.com/2009/09/17/snow-leopard-lacks-security-features-present-in-windows-vista-windows-7/) _on September 17, 2009._
