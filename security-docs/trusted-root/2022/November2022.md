---
title: November 2022 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in November 2022 to the root store.
ms.date: 11/29/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol
ms.topic: conceptual
---

# November 2022 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, November 29, 2022, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **NotBefore** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. TrustCor	\\ TrustCor ECA-1	\\ 58D1DF9595676B63C0F05B1C174D8B840BC878BD
2. TrustCor \\ TrustCor RootCert CA-1	\\ FFBDCDE782C8435E3C6F26865CCAA83A455BC30A
3. TrustCor \\ TrustCor RootCert CA-2	\\ B8BE6DCB56F155B963D412CA4E0634C794B21CC0


>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
