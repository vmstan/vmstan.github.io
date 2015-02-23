---
layout: post
title: VMware (Horizon) View 5.2
date: '2013-02-25 18:00:00'
---

VMware tacked an extra word onto the name of the product, so it's officially VMware Horizon View 5.2. There's a good rundown of whats new at [Andre Leibovici's blog](http://myvirtualcloud.net/?p=4627) but among my favorites are:

  * View Composer will use SEsparse on VMFS volumes to run through and eliminate unused space in Linked Clones	
  * 3D hardware accelerator support, so virtual machines can use physical GPUs, that is also vMotion friendly (can be moved to non-GPU enabled hosts)
  * Lync 2013 support
  * Windows 8 support (with multi-touch support as well)
  * Pools larger than 8 hosts (can go to 32 now) and up to 10,000 desktops (previously 2,000)
  * Multi-VLAN support, can use View to assign different port groups on the same base image
  * 2X improvement in recompose/refresh times
  * Integration with vCenter Web Client for basic functions
  * Revamped View Administrator to match look and feel of new vCenter Web Client
  * Support for vCenter Appliance
  
Looking forward to getting my hands on this (and my first implementation.)
