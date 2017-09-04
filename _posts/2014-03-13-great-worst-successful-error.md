---
layout: post
title: Great worst successful error
date: 2014-03-13 01:09
featured_image: /images/8ece4-0puaerxxkximnzdbj.png
featured_alt: Success!
---

There is a bug in Windows Server 2012 R2 in the volume license activation wizard, that if you don’t change the Key Management Service port setting when applying the configuration (from “0” to whatever you want it to be, such as the default of 1688) you get this absolutelty most unhelpful success/error message.

    The following error has occurred. Please resolve the error and try again. Description: STATUS_SUCCESS
