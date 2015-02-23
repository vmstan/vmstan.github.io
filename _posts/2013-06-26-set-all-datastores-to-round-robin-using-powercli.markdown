---
layout: post
title: Set all datastores to round robin using PowerCLI
date: '2013-06-26 17:00:00'
---

So you want to set your datastores to Round Robin, but you've got multiple hosts, dozens of datastores, and very little time? Just fire up PowerCLI and run this script. Replace "VMCluster" with the name of your cluster. This will change the multi pathing policy on each datastore, on each host in the cluster.

	get-cluster “VMCluster” | Get-VMHost | Get-ScsiLun -LunType disk | Where-Object {$_.MultipathPolicy -ne “RoundRobin”} | Set-ScsiLun -MultipathPolicy “RoundRobin”	

A great overview of Round Robin vs Fixed multipathing, specifically on vSphere 5.1 and EMC storage, and why you should be using it, can be found over at [vElemental](http://velemental.com/2012/09/07/fixedround-robin-in-5-1-and-a-simple-powercli-block-pathing-module/).