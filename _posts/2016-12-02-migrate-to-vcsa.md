---
layout: post
title: Migrate to VCSA
date: 2016-12-02 20:21
author: marshalus
comments: true
categories: [Linux, Uncategorized, Vmware, Windows]
---



Last night I did my first customer migration from a Windows based vCenter to the VMware vCenter Server Appliance (VCSA) using the new 6.0 U2M utility.

The customer was previously running vCenter 5.1 GA on a Windows Server 2008 R2 based physical HP host. In order to migrate to the VCSA, we first had to do two in place upgrades of vCenter from 5.1 GA to 5.1 U3, then again from 5.1 U3 to 5.5 U3d. After that, onto the VCSA migration.

Given the length of time the system was running on 5.1 GA code (ouch) and the amount of step upgrades required just to get things cleaned up, there was some cause for nervousness.

I admit, even though I’d read up on it, tested it in a lab, and heard other success stories … I still expected my first try to be kind of a mess.

<figure class="wp-caption">![](https://vmstanblog.files.wordpress.com/2016/12/866f7-1czoys1rovqn-3wvb1dg4sq.png)

<figcaption class="wp-caption-text">Migration in Progress</figcaption>

</figure>

But, it was not. The entire migration process took around 30 minutes, and was nearly flawless.

[embed]https://twitter.com/vmstan/status/804521366745731072[/embed]

I had more issues with the upgrade from 5.1 to 5.5 than anything else during this process. Somewhere during that 5.5 upgrade the main vCenter component quit communicating with the SSO and inventory service. There were no errors presented during the upgrade, but it resulted in not being able to login at all through the C# client, and numerous errors after eventually logging in as administrator@vsphere.local to the Web Client.

I tried to run through the [KB2093876](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=2093876) workarounds, but was not successful. I ended up needing to uninstall the vCenter Server component, remove the Microsoft ADAM feature from the server, and then reinstall vCenter connected to the previous SQL database. Success.

Given those issues, I was nervous about the migration running into further issues, mostly from the old vCenter.

But again, it worked as advertised.

After the migration I did notice the customer’s domain authentication wasn’t working using the integrated Active Directory computer account. After adjuting the identity provider to use LDAP, it worked fine. I’ve had this happen randomly enough on fresh VCSA installs to think its something to do with the customer environment, but I was under the wire to get things back up and felt there was no shame in LDAP.

[embed]https://twitter.com/lamw/status/804688216791994368[/embed]

I’ve done too many new deployments of the VCSA since 5.x to count, and at this point was already pretty well convinced there was no reason for most of my customers to deploy new Windows based vCenters. I’d also done a fair bit of forklift upgrades with old vCenters where we ditch everything to deploy a new VCSA, which isn’t elegant, but it works if for my smaller customers that still don’t yet have anything like View, vRA, SRM, integrated backups/replication, etc.

Now I’m confident that any existing vCenter can be successfully migrated.

**Windows vCenters, physical and virtual: I’m coming for you.**