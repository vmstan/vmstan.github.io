---
layout: post
title: RPA ‘Factory Reset’
date: 2015-04-14 16:47
permalink: /rpa-factory-reset-b5c6dde9a520
---


I ran into a situation recently where the need arose to effectively “factory reset” an Generation 5 EMC RecoverPoint Appliance (Gen 5 RPA). In my case, I had one RPA where the local copy of the password database had become corrupted, but the other three systems in the environment were fine. There was nothing physically wrong with the box, I just wanted to revert it back to new and treat it like a replacement unit from EMC, and rejoin it back to the local cluster.

From what I could find, EMC had no documented procedure on how to do this. So after finding a blog entry and EMC Communities post (that individually did not help) here it is:

*   Attach a KVM to the failed appliance and reboot.
*   Hit F2 to boot into the system BIOS (the password emcbios).
*   Under USB settings, **Enable Port 60/64 Emulation**.
*   Save your settings and reboot the appliance.
*   This time hit Ctrl + G to enter the RAID BIOS.
*   Select the RAID 1 virtual drive and start a Fast Init.
*   Reboot the appliance.
*   Hit F2 to boot back into the system BIOS.
*   Under USB settings, **Disable Port 60/64 Emulation**.
*   Reboot the appliance and verify that no local OS is installed.
*   Insert the RecoverPoint install CD (the one you created after you downloaded the ISO from EMC Support and after you’ve burned it) and press enter to start the install.
*   The installation does not require any user interaction, your appliance will reboot when its competed into a “like new” status.
*   Rejoin the appliance to the cluster using procedures generated from Solve Desktop. (You can ignore instructions about rezoning fibre channel connections, or spoofing WWPNs, since none of this will have changed.)

The key points here are the bits about Port 60/64 Emulation. If you don’t do this, the RAID BIOS will load to a black screen and take you nowhere. Likewise, if you leave it enabled your RecoverPoint OS may not install correctly.
