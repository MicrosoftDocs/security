---
title: August 2024 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in August 2024 to the root store.
ms.date: 7/9/2024
ms.service: security
author: tahmad2
ms.author: tahminaahmad
ms.topic: conceptual
---

# August 2024 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, August 27, 2024, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will NotBefore the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):

* e-commerce monitoring GmbH // GLOBALTRUST 2020 // D067C11351010CAAD0C76A65373116264F5371A2

**Certificate Transparency Log Monitor (CTLM) policy** <br />
The Certificate Transparency Log Monitor (CTLM) policy is now included in the monthly Windows CTL. It's a list of publicly trusted logging servers that is for validating certificate transparency on Windows. The list of logging servers is expected to change over time as they're retired or replaced, and this list reflects the CT logging servers that Microsoft trusts. In the upcoming Windows release, users are able to opt in to certificate transparency validation, which will check for the presence of two Signed Certificate Timestamps (SCTs) from different logging servers in the CTLM. This functionality is currently being tested with event logging only to ensure it's reliable before individual applications can opt in to enforcement.

>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
