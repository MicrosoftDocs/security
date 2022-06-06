---
title: September 2020 Deployment Notice for Microsoft Trusted Root Program 
description: This document provides details about the changes made to the root store in September 2020.
ms.date: 08/18/2020
ms.service: security
ms.author: dansimp
author: dansimp
ms.topic: conceptual
---

# September 2020 Deployment Notice for Microsoft Trusted Root Program 

On Thursday, September 3rd, 2020, Microsoft will release an update to the Microsoft Trusted Root Certificate Program.

This release will **add the IP Security IKE EKU** to the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Austrian Society for Data Protection (Arge Daten) (GlobalTrust) \\ 		GLOBALTRUST	 \\ 	342CD9D3062DA48C346965297F081EBC2EF68FDC
2. China Financial Certification Authority (CFCA) \\ 	CFCA EV ROOT \\ 		E2B8294B5584AB6B58C290466CAC3FB8398F8483
3. Chunghwa Telecom	 \\ 	Chunghwa Telecom Co., Ltd. - ePKI Root Certification Authority	 \\ 	67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0
4. Entrust \\ 		AffirmTrust Premium	 \\ 	D8A6332CE0036FB185F6634F7D6A066526322827
5. Entrust \\ 		AffirmTrust Commercial	 \\ 	F9B5B632455F9CBEEC575F80DCE96E2CC7B278B7
6. Entrust \\ 		Entrust Root Certification Authority	 \\ 	B31EB1B740E36C8402DADC37D44DF5D4674952F9
7. Entrust \\ 		AffirmTrust Premium ECC	 \\ 	B8236B002F1D16865301556C11A437CAEBFFC3BB
8. Entrust \\ 		Entrust.net Certification Authority (2048)	 \\ 	503006091D97D4F5AE39F7CBE7927D7D652D3431
9. Entrust \\ 		Entrust Root Certification Authority - G2	 \\ 	8CF427FD790C3AD166068DE81E57EFBB932272D4
10. Entrust \\ 		AffirmTrust Networking	 \\ 	293621028B20ED02F566C532D1D6ED909F45002F
11. Izenpe S.A. \\ 		Izenpe.com \\ 		30779E9315022E94856A3FF8BCF815B082F9AEFD



>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus> 
