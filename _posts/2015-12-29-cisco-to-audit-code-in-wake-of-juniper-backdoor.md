---
layout: post
title: Cisco to audit code in wake of Juniper backdoor
date: 2015-12-29 08:55
---


#### This step is a preventative measure for Cisco and is not in response to a known weakness

In the wake of [an announcement by Juniper](https://www.petri.com/juniper-finds-backdoor-exposing-encrypted-vpn-traffic) that after an internal code audit, they had uncovered two backdoors in the operating systems used in their NetScreen firewalls, Cisco has announced that they’re taking similar steps to perform an audit of their code.

<figure>![](https://vmstanblog.files.wordpress.com/2015/12/4dc97-1dmu8q3fj6n_qo9xosnr7pa.jpeg)</figure>

In [a blog post](http://blogs.cisco.com/security/update-for-customers) by Anthony Grico, Senior Director of the Security and Trust Organization within Cisco, the company outlines that although their normal development practices should detect unauthorized code from sneaking into their products, no process can eliminate all risk. The company will be conducting penetration testing and code reviews.

The company also says that there has been no indication that any code has been compromised, that the review was launched as a proactive effort in the wake of Juniper’s bulletin, and also not in response to any outside request.

It’s generally acknowledged by security experts that due to the level of sophistication of such attacks against companies like Cisco and Juniper, it’s likely state agencies are responsible for the unauthorized code; the Chinese military, the US’s NSA or the UK’s GCHQ. The NSA had an operation exposed by Edward Snowden in which they intercepted Cisco products, mid-shipment, that were destined for other countries, to install backdoor code directly into those routers, firewalls, etc.

However, it may be also be less sophisticated attackers (or governments) who are using existing backdoors. Matthew Green, a cryptographer and professor at Johns Hopkins University, [has theorized](http://blog.cryptographyengineering.com/2015/12/on-juniper-backdoor.html) that the Juniper VPN decryption vulnerability may have been the result of Juniper’s implementation of an altered version of the NSA’s backdoored Dual EC random number generator. As Green explains, encryption depends on unpredictable random number generators, and the Dual EC method that has been advised by the National Institute of Standards and Technology (NIST) since the early 2000s was discovered by researchers to include a (probably NSA inserted) weakness that allowed an attacker to decrypt intercepted traffic.

Juniper utilizes Dual EC, but in a non-standard way so that the (NSA) backdoor was removed. However, researchers who decompiled Juniper’s firmware packages, have compared the differences in the compromised code and found that the compromised sections altered the number generator so that anyone with knowledge of the effected code, could again decrypt traffic.

In effect, the attackers used an existing (closed) door to open a new one for their own use.

* * *

_Originally published at_ [_www.petri.com_](https://www.petri.com/cisco-to-audit-code-in-wake-of-juniper-backdoor-announcement) _on December 29, 2015._
