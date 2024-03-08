---
title: January 2021 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in october 2020 to the root store.
ms.date: 1/20/2021
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# January 2021 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, January 26, 2021, Microsoft will release an update to the Microsoft Trusted Root Certificate Program.

This release will **add** to the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. 	Telia Company \\ Telia Root CA v2 \\ B999CDD173508AC44705089C8C88FBBEA02B40CD

This release will **add the Code Signing** to the following roots:
1. 	Atos \\ Atos TrustedRoot 2011 \\ 2BB1F53E550C1DC5F1D4E6B76A464B550602AC21

>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus> 
