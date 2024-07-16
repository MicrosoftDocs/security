---
title: Testing  - Microsoft Trusted Root Certificate Program
description: This document provides details about the changes made monthly to the root store.
ms.date: 02/15/2024
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# Testing Instruction - Microsoft Trusted Root Certificate Program

Before releasing a new Certificate Trust List (CTL) to production, Microsoft requests that Certificate Authorities who have requested additions or changes to the CTL validate that the changes they expect are present. Testing is also available to any users of the operating system. Changes are generally posted one week before the release on the test server. 

To achieve this, the user will need to make the following modifications to a PC running Windows: 


## Testing Configuration
1. Within the Windows registry, change [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\systemCertificates\AuthRoot\AutoUpdate] "RootDirUrl" to http://ctldl.windowsupdate.com/msdownload/update/v3/static/trustedr/en/test

2. Delete the following registry keys
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\EncodedCtl]
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\LastSyncTime]
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\Certificates] (deleting all cached certificates)

 

 
## Reset to Normal Configuration
1. Within the Windows registry, change [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\systemCertificates\AuthRoot\AutoUpdate] "RootDirUrl"  to http://ctldl.windowsupdate.com/msdownload/update/v3/static/trustedr/en (note it is the same without the test at the end)

2. Delete the following registry keys
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\EncodedCtl]
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\AutoUpdate\LastSyncTime]
 * [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates\AuthRoot\Certificates] (deleting all cached certificates)
 
Please note, deleting these registry keys can also force an update of the CTL at any time. 
