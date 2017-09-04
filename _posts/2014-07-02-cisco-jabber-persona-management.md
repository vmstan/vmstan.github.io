---
layout: post
title: Cisco Jabber & Persona Management
date: 2014-07-02 15:32
---


I just got finished with a customer issue who had deployed Cisco Jabber along with VMware View, using Persona Management and floating desktops set to refresh at logoff. Much to their annoyance, users would have to reconfigure their Cisco Jabber client with the server connection settings and any client customizations made were lost after logging back in to the desktops.

After looking into this, what it looked like was happening was that the Jabber configuration XML files were not being sync’d down to the local PC before the Jabber client was launching and this was causing the settings to default back to a non-setup state. Even though the configuration data stored in jabberLocalConfig.xml was saved to the Persona Management share it never had a chance to get loaded before it was overwritten.

![](/images/45281-0kmvhljy_-krcsley.png)

The issue was resolved by adjusting Persona Management group policies to precache the settings stored on the persona share to the virtual desktop before completing login.

Modify the Persona Management GPO setting “Files and folders to preload” to include the following directory:

    AppDataRoamingCiscoUnified CommunicationsJabberCSF

Server settings, custom adjustments to the client are now maintained across desktop sessions. WIN!
