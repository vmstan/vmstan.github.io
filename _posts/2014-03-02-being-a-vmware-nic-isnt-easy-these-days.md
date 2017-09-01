---
layout: post
title: Being a VMware NIC isn’t easy these days
date: 2014-03-02 21:28
---


Life is rough for a ESXi network card these days, both pNIC and vNIC. It’s especially bad if you’re using E1000/E1000e adapters in your VMs, or using Broadcom network cards, or a combination of both.

And considering Broadcom cards are the built in pNIC adapters for nearly every piece of server hardware, and the E1000 driver is the default Windows Server vNIC adapter in VMware: these are two incredibly common things to have happen, so what environment isn’t using a combination of both?

On the physical NIC side, VMware has identified an issue with the tg3 drivers in use **since ESX 3.5** that can cause data corruption.

The options for resolution there are to upgrade the Broadcom driver on your hosts, or disable TCP Segmentation Offload on your cards.

On the virtual NIC side, VMware has identified an issue with the E1000 adapter that causes the purple screen of death on hosts with virtual machines using this adapter on anything running ESXi 5.0, 5.1 or 5.5.

Options for resolution are to convert virtual machines to another driver such as VMXNET3 or disable Receive Side Scaling inside the guest operating system.

For ESXi 5.1 hosts, Update 2 has been identified as having a fix for this issue, but doing so may introduce its own set of issues.

Again, the workaround is to use something like the VMXNET3 adapter in your virtual machines. You can also install patch ESXi510–201402001 after installing Update 2 to fix the memory leak that causes the second issue.

Unless you can’t do so for an incompatibility reason I would suggest using VMXNET3 as your default vNIC adapter as best practice. If you have the ability to isolate E1000 virtual machines to a host or subset of hosts within your cluster to prevent a crash from effecting other systems, I would also do this.
