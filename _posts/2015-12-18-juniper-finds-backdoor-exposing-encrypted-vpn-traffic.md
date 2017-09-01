---
layout: post
title: Juniper finds backdoor exposing encrypted VPN traffic
date: 2015-12-18 10:52
author: marshalus
comments: true
categories: [Networking, Nsa, Security, Uncategorized]
---


In [a security advisory](http://forums.juniper.net/t5/Security-Incident-Response/Important-Announcement-about-ScreenOS/ba-p/285554) posted late Thursday, Bob Worrall, Juniper Network’s Chief Information Officer, announced that the ScreenOS software used on the company’s NetScreen firewalls contains an unauthorized backdoor allowing third parties to potentially monitor encrypted VPN traffic.

“During a recent internal code review, Juniper discovered unauthorized code in ScreenOS that could allow a knowledgeable attacker to gain administrative access to NetScreen devices and to decrypt VPN connections. … At this time, we have not received any reports of these vulnerabilities being exploited,” Worrall wrote.

Juniper says that ScreenOS versions 6.2.0r15 through 6.2.0r18 and 6.3.0r12 through 6.3.0r20 are affected should be upgraded immediately to either 6.2.0r19 or 6.3.0r21, as there are no workarounds to disable access. Juniper also says they have no evidence that the their products running their Junos operating system are impacted by this breach.

In [another knowledgebase article](http://kb.juniper.net/InfoCenter/index?page=content&id=JSA10713&actp=search), Juniper explains what type of logged event may appear on a compromised system, but warns that a skilled attacker would likely be able to clean his tracks and remove the events from the logs.

While it’s not clear who is responsible or how this backdoor was added to the code, many security experts point to a [2013 article published by Der Spiegel](http://www.spiegel.de/international/world/catalog-reveals-nsa-has-back-doors-for-numerous-devices-a-940994.html) that said an NSA operation called FEEDTHROUGH worked specifically against Juniper firewalls and gave the agency persistent backdoor access.

The NSA also had an operation exposed by Edward Snowden in which they intercepted Cisco products, mid-shipment, that were destined for other countries, to install backdoor code directly into those routers, firewalls, etc. However, unlike that operation, if the NSA were to be responsible for the Juniper backdoor, this exploit would be present on any ScreenOS hardware around the world, including within the United States.

* * *

_Originally published at_ [_www.petri.com_](https://www.petri.com/juniper-finds-backdoor-exposing-encrypted-vpn-traffic) _on December 18, 2015._