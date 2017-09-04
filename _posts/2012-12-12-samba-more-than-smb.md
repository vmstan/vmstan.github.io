---
layout: post
title: Samba, more than SMB
date: 2012-12-12 18:00
external_url: https://www.samba.org/samba/news/releases/4.0.0.html
host: Samba.org
---


> _Samba 4.0 comprises an LDAP directory server, Heimdal Kerberos authentication server, a secure Dynamic DNS server, and implementations of all necessary remote procedure calls for Active Directory. Samba 4.0 provides everything needed to serve as an Active Directory Compatible Domain Controller for all versions of Microsoft Windows clients currently supported by Microsoft, including the recently released Windows 8.

This is certantly interesting, I didn’t realize this was in development, but the latest version of Samba (the popular free open source implemenetation of the Windows file sharing protocols) now lets you run a true open source equal to Microsoft Active Directory.

If someone were to bundle a Linux OVA file with this new Samba domain controller code, along with the vCenter Server Appliance (based on Linux), and the VMware Web Client, the reliance on Microsoft Windows servers to have a functional VMware environment is eroding.
