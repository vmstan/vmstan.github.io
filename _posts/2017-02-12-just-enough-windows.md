---
layout: post
title: Just enough Windows
date: 2017-02-12 00:57
permalink: /just-enough-windows-fece0fcb6186
---

I’ve not been a true “Windows user” on a daily basis since the glorious afternoon my first MacBook Pro arrived in 2011. That didn’t exactly mean I quit using Windows on that day, but over time I’ve continued to slim down my actual needs of the Windows desktop operating system to the point where now I keep a Windows VM around for “just enough” of the things I need from it.

Windows 10 is a huge advancement over Windows 7, which is where I left off as a PC user and over these last six years Microsoft has learned a lot from Windows 8.x being such a mess. But Windows 10 is an OS intended for use on everything from 4" smartphones to watercooled gaming rigs with multiple 27" 4K displays.

In this guide I’ve focused on simple methods of stripping out a lot of the things that don’t apply to virtual machine usage, and some of the cruft that is really only useful for someone running it on a daily driver. Typically I can reduce the idle memory and disk footprint by about 25% without loss in necessary functionality.

These instructions are not all specific to VMware Fusion, but some are. This also isn’t designed to be the “ultimate guide” in Windows 10 performance, space savings, or anything else. It’s a quick and clean way to do most of those things but not all encompassing. I think it’s easy for some of those types of optimization guides to focus on getting Windows to the point where it’s so lacking it’s almost unusable or starts breaking core functions.

This is a “light” optimization for my usage. It could it yours as well, if you have similar needs like running a small collection of utility type applications, such as a couple of EMC product deployment tools, or the old VMware client.

<!--more-->

![](/images/27487-1lknvkdktmelm5lknlbtlmw.png)

### What edition of Windows 10

Start with a fresh download of Windows 10\. Microsoft spins updated copies fairly regularly, so if you’ve not got one based on the 1607 build, start there.

In terms of editions, if you have access to the Windows 10 LTSB (Long Term Servicing Branch) then I suggest using that. The LTSB is updated less frequently with the latest features from Microsoft, but in my mind that’s just perfectly fine because we’re not concerned about features, just basic core OS functionality, stability and security.

If you don’t have access to the LTSB, another option is to download the evaluation of Enterprise and reinstall your VM every 120 days. It seems like I do this already as a matter of habit anyway.

The last option is to grab a copy of Home or Professional. Either one. Nothing we are doing here really needs the Professional features. I just like the LTSB and Enterprise for their lack of preinstalled bullshit, like Candy Crush.

One of the things you don’t get in the LTSB is the Microsoft Edge browser. If you have a need for that, such as browser testing on websites, then don’t use it.

### Creating the VM

So fire up VMware Fusion and create a new VM using your freshly downloaded ISO.

*   **Uncheck Easy Install**, because life shouldn’t have an easy button.
*   **Customize Settings**, I usually give my VM 2 vCPU/cores and 2.5GB of RAM.
*   **Disable 3D Graphics,** if you have a discrete NVIDIA or AMD processor in your Mac laptop, this will generally prevent it from engaging with your VM running on battery power and easily give you another hour of work time.

#### Advanced VM Settings

**Option + Right Click** on VM in the Library and select **Open Config File in Editor.**

*   Enable support for EFI based booting, instead of BIOS.
*   Replace the E1000 network card with a more efficent VMXNET3

``` ini
firmware = "efi"
ethernet0.virtualDev = "vmxnet3"
```

### Installing Windows

Power on and run through the GUI installer as normal. After the files get laid out to the disk and the first reboot happens, you’ll begin getting configuration choices.

Do not use Express Settings, and set the following customized options:

*   Disable all of the personalization options
*   Disable all of the location options
*   Disable all of the connectivity and error reporting
*   Disable all of the browser protection options

Set a local username, if you’re not using Enterprise you have to jump through a couple hoops to tell it not to connect your login to a Microsoft account, but it’s worth it.

After the installer processes complete, you’re dumped to a halfway functional desktop. Perform your standard VMware Tools install to get all your network and display drivers, reboot.

![](/images/286d2-1n0yt_1ofk2ymqptsvxyj4w.png)

Drop in your license key to activate Windows and then run Windows Update, reboot. Unlike prior versions of Windows, updating a new Windows 10 installation isn’t usually a horrible cycle of download 147 packages to update, reboot, update more, reboot again, update even more, reboot, process. Kudos to Microsoft on that.

After installing updates and rebooting it was necessary for me to run a repair process on my VMware Tools. I’ve never had that happen before, so it could be an issue with a recent update.

Enable sharing between your VM and Mac downloads folder, I don’t like sharing the other folders because I only rarely use them from Windows and don’t like them messing with my Mac files. I also have an SD card in my Mac with archived installers and such, so I share that as well.

Before we run our optimization tools, **Enable .Net 3.5 from Windows Features** because you’ll need them for the first tool we’re about to run.

### Optimization and Privacy

#### Run [Tron](https://www.reddit.com/r/TronScript/comments/5t1zcc/tron_v1000_20170209_add_wsus_offline_support_add/) 

This will automate the cleanup and removal of junk that Microsoft has in Windows that we’re not going to use.

![](/images/934a7-1q95dth3fgki2c6ykahatya.png)

The Tron process takes a long time. The script says 4 hours, I don’t find it to be quite that long, but it’s a while. This will run a lot of stuff you don’t necessarily need, like performing anti-malware scans against the system. They won’t take super long since the VM itself is pretty basic at this point, but if you’re pressed for time you can look into CLI options to disable them. Otherwise I just set it and forget it. I went and got a haircut while my copy ran. Overall, it took around an hour.

Reboot

#### Run [Blackbird](http://www.getblackbird.net/documentation/) 

This will privatize your Windows setup. This should disable most of the Microsoft telemetry, call home and tracking stuff built into Windows 10.

It’s not that I’m really super paranoid that Microsoft is going to spy on me (mostly the NSA, through Microsoft) but disabling a lot of this should cut down on system overhead.

Plus, yeah, privacy.

![](/images/1fc5d-1f0dowknovp6uvvml6agiew.png)

Blackbird should only take a few minutes to apply.

Reboot

#### Uninstall, Uninstall, Uninstall

Uninstall built in applications under Control Panel > System > Apps.

If you’re using a consumer version of Windows there will be a lot more here, like the “metro” Mail app, Calendar, etc. Get rid of them. The LTSB version has almost none of these, which is one reason I like it. I uninstall OneDrive. Malwarebytes was installed by Tron, if you want to keep it on the system, that’s fine, but I just uninstalled it.

#### Disable unneeded features

*   Media Features
*   Print to PDF
*   Internet Printing
*   Fax & Scan
*   SMB 1.0
*   Remote Differential Compression API Support
*   Work Folders
*   XPS Services & Viewer

Your milage my vary here. If you connect to a lot of Windows 2000/2003 based shares or have to manage a lot of faxes, act accordingly.

![](/images/c8b7f-1iln7clrcrelrzubks18dog.png)

An interesting one to remove would be Internet Explorer. I typically use Firefox or Chrome in my Windows VM. If it’s problematic not to have IE installed as well (especially when you don’t have the built in Edge browser from the LTSB install) you can always reinstall it later.

As for PowerShell you’ll likely want to keep this, especially in order to install and run VMware PowerCLI.

#### Run the** [**VMware OS Optimization Tool**](https://labs.vmware.com/flings/vmware-os-optimization-tool)

This tool is designed to run in VMware View desktops, and so while the overwhelming majority of the changes this tool makes are beneficial to us, there are a few things that I adjust to accommodate for the fact that this is one VM that I’ll be using, and not a template VM that will be used to roll out 1000 clones in a shared environment.

![](/images/aae0b-1ymbzkbm1jlnrfhrppzdl0g.png)

*   Leave the Windows Firewall enabled, unless you really don’t like firewalls.
*   Leave UAC enabled, unless you really hate UAC.
*   Leave Windows Defender enabled, unless you don’t like it and want to use something else.
*   Leave Security Center enabled, unless you don’t get the point of the last three suggestions.

Check all of the app removals you don’t want, if any of them are still there at this point.

Reboot

### Wrapping Up

At this point you should only really be left with a core Windows system. During one of the optimizations, Windows Updates may have been disabled. Open up the services.msc utility and check, if it is, enable it … unless you don’t like patches.

Shut down the VM

Run a disk reclamation on the VM to free up about 3GB of space.

![](/images/f01ce-1ftiuskxrtohyu7q8zwqnpw.png)

I go ahead and set my VM hard drive not to go to sleep, because most of the time I have it open it’s being used for a purpose, and I will manually suspend the VM in Fusion when it’s no longer needed. Sometimes I have to use the VM to run updates on EMC VNX systems using Unisphere Service Manager that can take hours at a time. I don’t want the VM to accidently sleep during this time.

A useful tool on the macOS side to prevent your overall system from going to sleep during these activities is a free tool called [Amphemetine](https://itunes.apple.com/us/app/amphetamine/id937984704?mt=12). You can set it to keep the system alive as long as an application (like VMware Fusion) is running, indefinitely or on a timer.

From this point it’s a matter of installing my utility applications.

*   Java. Yeah, I know.
*   EMC Unisphere Service Manager
*   VNX Initalization Assistant
*   VNXe & Unity Connection Utility
*   EMC RecoverPoint Deployment Manager
*   VMware vSphere “C#” Clients
*   VMware vSphere PowerCLI

![](/images/d7243-1bfqyeegipckby4zv5m-tag.png)
