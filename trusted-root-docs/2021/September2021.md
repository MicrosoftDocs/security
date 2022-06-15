---
title: September 2021 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in September 2021 to the root store.
ms.date: 6/3/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol-ms
ms.topic: conceptual
---

# September 2021 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, September 28, 2021, Microsoft released an update to the Microsoft Trusted Root Certificate Program.


This release will **add Client Authentication EKU** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Internet Security Research Group(ISRG)	\\ ISRG Root X1	\\ CABD2A79A1076A31F21D253635CB039D4329A5E8
2. Internet Security Research Group(ISRG)	\\ ISRG Root X2	\\ BDB1B93CD5978D45C6261455F8DB95C75AD153AF


>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
