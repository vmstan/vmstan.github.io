---
layout: post
title: Clone VM from snapshot
date: 2015-01-08 17:01
---


Have you ever wanted to easily clone a virtual machine from a snapshot, and have the clone reflect the source as it existed at that point in time, as opposed to the current status of the source? Jonathan Medd ([@jonathanmedd](https://twitter.com/jonathanmedd/)) has a great [PowerCLI script](http://www.jonathanmedd.net/2013/07/clone-a-vm-from-a-snapshot-using-powercli.html) that I found yesterday, to do exactly this.

Copy the contents of his script into a new .ps1 file, save it, and then execute the script within a PowerCLI window to add the function to your session.

    . C:PowerCLIScriptsNewVMFromSnapshot.ps1

Then run the new function to create your clones. By default it uses the last snapshot in the chain, but you can request a snapshot by name as explained on his site.

    New-VMFromSnapshot -SourceVM VM01 -CloneName "Clone01" -Cluster "Test Cluster" -Datastore "Datastore01"
