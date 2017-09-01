---
layout: post
title: Crashing ESXi with Cisco RAID controllers
date: 2016-11-30 16:34
---


Recently I had two VMware Horizon View proof of concept setups for work, where we designed an all in one Cisco UCS C240 M4 box, full of local SSD and spindles, in various RAID sets. This lets the customer kick the tires on View in a small setup to see if its a good fit for their environment, but on something more substantial than cribbing resources from the production environment.

<figure>![](https://vmstanblog.files.wordpress.com/2016/11/b0550-1tvwnp9iow_upjucztazejg.png)</figure>

*   5x 300GB 10K SAS RAID 5 for Infrastructure VMs (vCenter, View Broker/Composer, etc)
*   10x 300GB 10K SAS RAID 10 for VM View Linked Clones
*   6x 240GB SSD RAID 5 for View Replicas
*   1x hot spare for each drive type
*   VMware ESXi 6.0 U2 is installed on a FlexFlash SD pair

After getting all the basics configured, we had a single View connection broker, with another View Composer VM on a local SQL Express 2012 instance for the database. Both were version 7.0.2\. At the first site the VM base image we attempted to deploy was an optimized Windows 7 x64 instance.

But under any sort of load during a deployment of more than a handful of desktops, the entire box would come to a total stop. In some cases the only way to restore any functionality was to pull the power and restart the infrastructure VMs, one by one. Of course, once the broker and composer instances were connected, they’d attempt to create more desktops and the cycle would continue. In an attempt to isolate the issue, we tried various versions of the VMware Tools, a new Windows 7 x86 image, and I even duplicated the behavior by building a nearly identical View 6.2.3 environment, within the same box.

After digging through the esxtop data as clones were being created, I could see KAVG/Latency across all RAID sets jumps to as high as 6000ms right before all disk activity on the system eventually stops.

It didn’t matter what configuration I tried, it was present with a fresh install of ESXi 6.0 U2, and after applying the latest host patches. It was present on the out of box UCS firmware of 2.0(10), and with the stock RAID drivers from the Cisco ISO. It was present after updating the firmware, and the drivers. It also happened regardless of if the RAID controller write back cache was enabled/disabled for the various groups.

Cisco is very particular about making ESXi drivers for their components match their [UCS compatibility matrix](http://www.cisco.com/web/techdoc/ucs/interoperability/matrix/matrix.html), so before I decided to give TAC a call, I made sure (again) that everything matched exactly. TAC ended up reviewing the same logs, to determine if this was a hardware issue, and while they made a couple of suggestions for adjustments, they were not successful in diagnosing a root cause. Yet, they insisted based on what they were seeing that it was not a hardware issue.

With this particular customer, we were also impacted by a variety of issues relating to the health of the DNS and Active Directory environment. With that in mind, we decided to focus on fixing the other environmental issues and in the meantime, not overload the UCS box until a deeper analysis could be done.

#### On to the second install

A day or so into the second setup at another customer, and I encountered the exact same issues. This time with a Windows 10 x64 image, and View 7.0.2\. The same crazy latency numbers under any amount of significant load, until the entire box stopped responding.

The physical configuration differed slightly in that we were integrating the C-Series UCS into the customers fabric interconnects, so the firmware and driver versions were even more different than the first host which was a standalone configuration connected to the customer’s network. After digging into it again with a fresh brain, and more perspective, I found the cause.

I started looking through the RAID controller driver details again. In both cases, VMware uses the LSI_MR3 driver as the default driver for the Cisco 12G RAID (Avago) controller in ESXi 6.0 U2\. In both environments I verified that we were running the suggested driver versions based on the Cisco UCS compatibility matrix, and we were. So I started digging at this controller and wondered what VMware suggests for VSAN (keeping in mind we aren’t running VSAN at either site) and sure enough, they DO NOT suggest using the LSI_MR3 driver, but instead [list the “legacy” MEGARAID_SAS driver as their recommendation](http://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vsanio&productid=38642&vsanrncomp=true&vcl=true), for the exact same controller.

After applying the alternative driver, I’ve not been able to break the systems.

What is odd, is that this appears to be related specifically to Cisco’s version of the controllers.

This week I did a similar host setup (although not for View) using a bunch of local SSD/SAS drives in a Dell PowerEdge 730xd, with their 12G PERC H730 RAID cards (which from what I can see appear to be rebranded versions of the same controller) and [VMware’s compatibility matrix has the LSI_MR3 drivers listed](http://www.vmware.com/resources/compatibility/detail.php?deviceCategory=vsanio&productid=34853&vsanrncomp=true&vcl=true).

I left those drivers enabled, and the customer ran a series of agressive PostgreSQL benchmarks against the SSD sets, with impressive results, and no issues from the host.

So, long story short, if you’re using local RAID sets for anything other than some basic boot volumes that don’t need any serious I/O, with the Cisco 12G RAID controller, you don’t want to use the Cisco recommended drivers.

#### Installation instructions

*   [Download the new driver (for ESXi 6.0 U2)](https://my.vmware.com/group/vmware/details?downloadGroup=DT-ESX60-LSI-SCSI-MEGARAID-SAS-66081600-1OEM&productId=491)
*   Extract the .vib file from the driver bundle and copy it to a datastore on the host
*   Enable SSH on the host and connect to it via your terminal application of choice
*   Apply the driver from the SSH session and disable the old one.
*   Reboot the host
*   Reconnect via SSH, and run core adapter list command to verify it’s active

[https://gist.github.com/vmstan/ca4bb3e2e305174e278af9a63b6287b8](https://gist.github.com/vmstan/ca4bb3e2e305174e278af9a63b6287b8)

This should verify that your RAID controller (typically either vmhba0 or vmhba1 is now using the megaraid_sas driver. If the “UID” is listed as “Unknown” in this readout, it’s normal.
