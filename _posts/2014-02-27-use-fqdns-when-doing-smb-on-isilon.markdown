---
layout: post
title: Use FQDNs when doing SMB on Isilon
date: '2014-02-27 03:23:06'
---

I ran across this little interesting tidbit in an EMC Support article that I wasn't aware of previously. Using the fully qualified domain name of the EMC Isilon SMB server for file sharing on is necessary for proper load balancing and access:

> Always use the fully qualified domain name (FQDN) of a SmartConnect zone when accessing the cluster. If you attempt to use the short name, Windows hosts will attempt to use the NetBios name service (NBNS) to resolve the connection. Because NBNS uses broadcast pings on the network to determine what IP a host is located at, the Windows client will connect to the first node to respond, which might result in client connections not being evenly distributed across the cluster. Additionally, by using the NBNS services, you do not utilize Kerberos for authentication and authorization, and are required to use NTLM (NT LAN Manager) based services, which can lead to permission denied errors.

For the non-Isilon initiated, a SmartConnect Zone is how Isilon does load balancing across various nodes in the cluster. It's configured as a delegation zone in your DNS, that replies back with a different IP address coorisponding to a physical NIC on an Isilon node. Depending on licensing it can be configured to reply based on basic round robin, or by connection count, CPU or network utilization metrics. It's important that it functions correctly as not to potentally overload an individual network port and therefore an individual node as an entry point into the cluster when accessing data.

The EMC Support article where it's referenced ([emc14003900](https://support.emc.com/kb/16495)) is centered around integrating SMB on Isilon with DFS, but I would think the principles are the same for normal user/server UNC addressing. 

Even if it's not, I'd still consider it best practice to use the FQDN.