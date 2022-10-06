---
title: October 2022 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in October 2022 to the root store.
ms.date: 9/29/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol
ms.topic: conceptual
---

# October 2022 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, October 25, 2022, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **Remove NotBefore Property** from the following root (CA \ Root Certificate \ SHA-1 Thumbprint):
1. A-Trust	\\ A-Trust-Root-07 \\	1B1815AF925D140EFC5AF9A1AA55EEBB4FFBC561

This release will **Modify** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. E-Tugra	\\ E-Tugra Global Root CA RSA v3	\\ E9A85D2214521C5BAA0AB4BE246A238AC9BAE2A9
2. E-Tugra	\\ E-Tugra Global Root CA ECC v3	\\ 8A2FAF5753B1B0E6A104EC5B6A69716DF61CE284
3. Carillon Information Security Inc.	\\ Carillon PKI Services G2 Root CA 1 \\	EB9237B72076F8CC8BC13E7046F2FCABC18199D3

This release will **Add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Government of India, Ministry of Communications & Information Technology, Controller of Certifying Authorities (CCA)	\\ CCA India 2022	\\ a79e41380bab3ed7f5188d9a5209cefcb3ca6991
2. První certifikační autorita, a.s.	\\ I.CA Root CA/ECC 05/2022	\\ 702723132527203947e0a97829a0731372b03917
3. První certifikační autorita, a.s.	\\ I.CA TLS Root CA/RSA 05/2022	\\ 83e5e5de325414970b263011084456e5faa13ffa
4. První certifikační autorita, a.s.	\\ I.CA Root CA/RSA 05/2022	\\ 461fdd19e71cd4329aadf224dc8c8628cd10fae8


>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
