---
title: September 2022 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in September 2022 to the root store.
ms.date: 9/29/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol
ms.topic: conceptual
---

# September 2022 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, September 27, 2022, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **Add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Entrust \\ Entrust Code Signing Root Certification Authority - CSBR1	\\ 897424053a4a887ac098380291034d885c8714b9	
2. E-Tugra \\ E-Tugra Global Root CA RSA v3	\\ E9A85D2214521C5BAA0AB4BE246A238AC9BAE2A9	
3. E-Tugra \\ E-Tugra Global Root CA ECC v3 \\ 8A2FAF5753B1B0E6A104EC5B6A69716DF61CE284	
4. Carillon Information Security Inc. \\ Carillon PKI Services G2 Root CA 1 \\ EB9237B72076F8CC8BC13E7046F2FCABC18199D3		
5. Firmaprofesional, S.A. \\ Autoridad de Certificacion Firmaprofesional CIF A62634068	\\ 0BBEC2272249CB39AADB355C53E38CAE78FFB6FE	

This release will **Modify** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Microsec Ltd. \\ e-Szigno Root CA 2017 \\ 89D483034F9E9A48805F7237D4A9A6EFCB7C1FD1


>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
