---
layout: post
title: vCenter 5.1 doesn’t keep more than 30-days of data
date: '2012-12-30 18:00:00'
---

A rather frustrating bug if you’re someone who likes to track long term performance, that lives in the original release of 5.1, as well as the A and B releases.

> [Using vCenter Server 5.1: You see only the last 30 days of performance history in the 'past year' view.](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2042164)

This issue is caused by the logic in the current database stored procedures for vSphere 5.1 (GA, A and B). This logic can purge data beyond 30 days and leave the past month only.
