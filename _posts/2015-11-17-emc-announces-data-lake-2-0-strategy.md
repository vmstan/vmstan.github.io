---
layout: post
title: EMC announces Data Lake 2.0 strategy
date: 2015-11-17 09:59
featured_image: /images/e4730-12z1wc7pf74eftpkhipfn3q.jpeg
featured_alt:
---

Data Lake 2.0 is the next generation of the EMC Isilon portfolio. Isilon is EMC’s scale-out network attached storage product. Traditionally, Isilon OneFS runs on physical nodes, with the cluster scaling from roughly 30 TB of raw capacity, all the way up to 50 PB. The nodes are all connected across a redundant, private, Infiniband network. But next year, EMC will offer two more ways to utilize Isilon. In addition to the traditional setup, EMC will offer “Cloud Pools” and “IsilonSD Edge” products.

#### Software Defined

The IsilonSD Edge product is the eqivilant of an Isilon virtual edition. Instead of running Isilon’s OneFS operating system directly on EMC provided hardware, customers can utilize their own physical boxes, loaded up with disk, and run the Isilon software as multiple instances inside VMware ESXi.

There are some restrictions though, chiefly, the ESXi host operating systems must meet strict specifications. EMC will leverage the hardware compatibility list used by VMware’s VSAN product, to determine what will be a supported IsilonSD configuration. Each IsilonSD virtual node will have VMDK files running on the local storage of the ESXi hosts. Shared storage (even one provided by another EMC storage system like the VNX or VMAX) is not supported. Even though IsilonSD and VSAN will share the same HCL, it should be noted that IsilonSD does not leverage VSAN’s technologies in any way. The VSAN team has done extensive work with testing various storage controllers, solid state, and hard drive brands, so it makes sense for EMC to lean on their work.

IsilonSD is intended for small, remote or branch office, and it will be limited in that it won’t scale-out like its traditional Isilon. Like traditional Isilon, IsilonSD requires at least three instances to create a cluster, but is limited to a maximum of six VMs. Traditional Isilon can scale to 144 nodes (the largest Infiniband switch on the market has 144 ports.) IsilonSD is also limited to 36TB of raw capacity in the cluster.

IsilonSD comes in two licensing models. A fully licensed (and, importantly) EMC supported configuration, and a free edition.

#### Cloudy, with a chance of RAIN

CloudPools allows administrators to leverage off site “cloud” disk targets as storage for your files. Traditional Isilon has three tiers of disk/node types; high performance all solid-state S-nodes, general performance SSD/disk X-nodes, capacity focused disk based NL-nodes, and high density deep archving HD-nodes. Now you can think of your cloud storage target as the super-cold target for your files. CloudPools leverages rules to determine what type of data, or at what age, files are moved between tiers, or off-site.

End users will have no knowledge of where the files came from, but may see the latency associated with having to retrieve files from off-site instead of from disks located in the company data center. Administrators don’t have to manually move data between on-site or the cloud, as the tiering is automatically done through pre-set policies. Files sent to the cloud are encrypted both in transmission and at the target cloud, and then decrypted as they arrive back on the on-site Isilon cluster.

CloudPools will be able to leverage both public and private clouds offerings. Supported public clouds instead Amazon Web Service S3 and Microsoft Azure; support for VMware vCloud Air is intended for a future release. Private cloud offerings are limited to EMC’s Elastic Cloud Storage solution.

All of this forms EMC’s “Data Lake” — an edge to cloud file storage strategy. IsilonSD Edge puts big data in remote locations, and makes it easily accessible and consumable to end users, with support for Isilon’s SyncIQ replication technology to keep a copy back in the data center for long term archiving, backup and disaster recovery. From there, data can be moved out to a cloud provider as files age out, to keep the speedy access available for more frequently used data.

EMC IsilonSD Edge, Isilon CloudPools, and the Isilon OneFS.Next version that will enable these functions is slated for availbility in early 2016.

* * *

_Originally published at_ [_www.petri.com_](https://www.petri.com/emc-announces-data-lake-2-0-strategy-isilon) _on November 17, 2015._
