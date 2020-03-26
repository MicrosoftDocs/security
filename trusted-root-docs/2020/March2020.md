---
title: March 2020 Deployment Notice  - Microsoft Trusted Root Program 
description: This document provides details about the changes made in March 2020 to the root store.
ms.date: 03/18/2019
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# March 2020 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, March 24th, 2020, Microsoft will release a planned update to the Microsoft Trusted Root Certificate Program.

This release will **add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):

1. Microsoft \\ Microsoft EV ECC Root Certificate Authority 2017 \\ 6B1937ABFD64E1E40DAF2262A27857C015D6228D
2. Microsoft \\ Microsoft EV RSA Root Certificate Authority 2017 \\ ADA06E72393CCBE873648CF122A91C35EF4C984D
3. Agence Nationale de Certification Electronique (ANCE) \\ TunTrust Root CA \\ CFE970840FE0730F9DF60C7F2C4BEE2046349CBB

This release will **remove the NotBefore status** of the following roots: 
1. Red Abogacía	\\ ACA ROOT \\ 496592B305707386CC5F3CDB259AE66D7661FCA


This release will **add the code signing EKU** in the following roots:

1.  IdenTrust \\	IdenTrust Commercial Root CA 1 \\ DF717EAA4AD94EC9558499602D48DE5FBCF03A25


>[!NOTE]
> * Windows 10 allows us to stop trusting roots or EKU's using the "NotBefore" or "Disable" properties, both of which allow us to remove certain capabilities of the root certificate without complete removal. These features are not available on versions prior to Windows 10. Earlier versions of Windows will be unaffected by this change. 
> * The NotBefore and Disable dates are set for the first day of the release month. This means that all certificates issued after March 1st will be affected.  
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus> 
