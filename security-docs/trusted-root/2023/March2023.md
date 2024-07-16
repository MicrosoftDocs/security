---
title: March 2023 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in March 2023 to the root store.
ms.date: 11/8/2023
ms.service: security
author: hasokol-ms
ms.author: hasokol
ms.topic: conceptual
---

# March 2023 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, March 28, 2023, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **Add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. 

This release will **Add EV SSL** from the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. 

>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
