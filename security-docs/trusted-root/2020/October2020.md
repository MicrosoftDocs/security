---
title: October 2020 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in october 2020 to the root store.
ms.date: 10/27/2020
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# October 2020 Deployment Notice - Microsoft Trusted Root Program 

On Thursday, October 27, 2020, Microsoft will release an update to the Microsoft Trusted Root Certificate Program.

This release will **NotBefore the Server Authentication** to the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. 	DATEV eG \\ CA DATEV BT 02 \\ 39410BC2303748066069A72A664DE4C743481296
2. 	DATEV eG \\ CA DATEV INT 02 \\ 93F7F48B1261943F6A78210C52E626DFBFBBE260
3. 	DATEV eG \\ CA DATEV STD 02 \\ AB9D58C03F54B1DAE3F7C2D4C6C1EC3694559C37



>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus> 
