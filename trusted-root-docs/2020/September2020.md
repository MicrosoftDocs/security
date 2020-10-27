---
title: September 2020 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in September 2020 to the root store.
ms.date: 09/29/2020
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# September 2020 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, September 29th, 2020, Microsoft will release a planned update to the Microsoft Trusted Root Certificate Program.

This release will **add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):

1. Austrian Society For Data Protection (GlobalTrust) \\ GLOBALTRUST 2020 \\ D067C11351010CAAD0C76A65373116264F5371A2
2. První Certifikační Autorita, A.S. \\ 	I.CA Root CA/ECC 12/2016 \\ 1E70283209903C9472C79B2C103E8EBB238BEB62
3. GlobalSign	\\ GlobalSign Root E46 \\ 39B46CD5FE8006EBE22F4ABB0833A0AFDBB9DD84
4. GlobalSign \\ GlobalSign Root R46 \\ 53A2B04BCA6BD645E6398A8EC40DD2BF77C3A290



>[!NOTE]
> * Windows 10 allows us to stop trusting roots or EKU's using the "NotBefore" or "Disable" properties, both of which allow us to remove certain capabilities of the root certificate without complete removal. These features are not available on versions prior to Windows 10. Earlier versions of Windows will be unaffected by this change. 
> * The NotBefore and Disable dates are set for the first day of the release month.   
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus> 
