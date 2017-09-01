---
layout: post
title: Don’t use a single 100mb vNIC
date: 2013-02-01 18:00
author: marshalus
comments: true
categories: [Networking, Uncategorized, Vmware]
---


![](https://vmstanblog.files.wordpress.com/2013/02/31116-0jw5z3dycff9kc-30.png)

1.  You really should never use 100mb networking with VMware for much of anything. I’m not even sure 100mb networking has any place in a modern datacenter, except maybe cheap connectivity to something like an iLO/DRAC.
2.  You should avoid using a single vNIC for any vSwitch, unless you just don’t care about things like load balancing or network redundancy.
3.  Not seen in the image, but Service Console/Management Network should not be on the same vSwitch as your VM Network port group. Good luck accessing your ESX host when all the bandwidth on your 100mb connection is used up by virtual machine traffic.
4.  The particular host in question did not have any vMotion setup, and/because there was no shared storage for the hosts in the “cluster” — term used loosely.
5.  Any combination of the above is grounds for removal of virtualization _privileges._
