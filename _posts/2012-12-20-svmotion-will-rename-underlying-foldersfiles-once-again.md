---
layout: post
title: svMotion will rename underlying folders/files, once again
date: 2012-12-20 18:00
author: marshalus
comments: true
categories: [Uncategorized, Vmware]
---


VMware has released Update 2 of vSphere 5.0, and among the fixes is one that should stand out as correcting the loss of a nice feature. Performing a Storage vMotion of a virtual machine will once again rename the underlying folder and VMDK files associated with the machine.

> **_vSphere 5 Storage vMotion is unable to rename virtual machine files on completing migration_**

In vCenter Server, when you rename a virtual machine in the vSphere Client, the vmdk disks are not renamed following a successful Storage vMotion task. When you perform a Storage vMotion of the virtual machine to have its folder and associated files renamed to match the new name. The virtual machine folder name changes, but the virtual machine file names do not change.

This behavior was present in the 4.x branch, and was annoyingly removed from 5.0\. Thankfully, VMware dropped it back in. Note that this feature is still missing from vSphere 5.1, but can only be assumed that it will be added in a future update release.