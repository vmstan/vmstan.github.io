---
layout: post
title: Faking an SSD drive in vSphere
date: 2013-01-17 18:00
external_url: http://www.yellow-bricks.com/2013/01/11/faking-an-ssd-in-your-virtualized-vsphere-lab/
host: Yellow Bricks
---

Notes on tricking VMware into thinking a datastore is actually an SSD drive. Very useful if you’re in a lab environment and want to just test some of the features in vSphere 5 that center around flash storage (but don’t have the funds to dedicate to actually having it.)

However it’s also useful if you actually have flash storage in a production environment but for some reason vSphere isn’t recognizing that fact.
