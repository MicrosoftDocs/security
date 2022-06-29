---
title: April 2021 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in April 2021 to the root store.
ms.date: 6/3/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol
ms.topic: conceptual
---

# April 2021 Deployment Notice - Microsoft Trusted Root Program 

On Thursday, April 29, 2021, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Digicert	\\ DigiCert CS ECC P384 Root G5	\\ 843573112A3B319344E5E4ECABC9F26C7CD54D07
2. Digicert	\\ DigiCert CS RSA4096 Root G5	\\ 5EEED86FA37C675230642F55C84DDBF67CD33C80
3. Digicert	\\ DigiCert TLS RSA4096 Root G5	\\ A78849DC5D7C758C8CDE399856B3AAD0B2A57135
4. Digicert	\\ DigiCert TLS ECC P384 Root G5	\\ 17F3DE5E9F0F19E98EF61F32266E20C407AE30EE
5. Digicert	\\ DigiCert SMIME RSA4096 Root G5	\\ 5BC5ADE29AA754DA848953A5FED75B4686D05708
6. Digicert	\\ DigiCert SMIME ECC P384 Root G5	\\ 1CB8A708C90D207901A0B2367FF09565E45324FE
7. Digicert	\\ DigiCert RSA4096 Root G5	\\ 87B8E6D38F1A39CD97F04A9E174B3C9EE7EE1115
8. Digicert	\\ DigiCert ECC P384 Root G5	\\ D1EEB1E8C09020BAB85D3DE27F78EE33A06CAEDB
9. Digicert	\\ DigiCert Client ECC P384 Root G5	\\ B218FE6D07952A2207A35AFD5ED8E4991029E336
10. Digicert	\\ DigiCert Client RSA4096 Root G5	\\ B60D92FC064D32AF1FEA30FCD85FB0243463A41C


This release will **NotBefore** the following roots:
1. Digidentity BV **	\\ Digidentity Services Root CA 	\\ 7B3FB277EE311C1ED560CAB96E4FED775E6A3EED
2. DATEV eG	\\ CA DATEV BT 02	\\ 39410BC2303748066069A72A664DE4C743481296
3. DATEV eG	\\ CA DATEV STD 02	\\ AB9D58C03F54B1DAE3F7C2D4C6C1EC3694559C37
4. DATEV eG	\\ CA DATEV INT 02	\\ 93F7F48B1261943F6A78210C52E626DFBFBBE260
5. Government of Spain, Ministerio de Trabajo e Inmigracion (MTIN) \\	AC1 RAIZ MTIN	\\ 6AD23B9DC48E375F859AD9CAB585325C23894071
6. Macao Post and Telecommunications eSignTrust Certification Authority \\	Macao Post eSign Trust	\\ 06143151E02B45DDBADD5D8E56530DAAE328CF90
7. QuoVadis	\\ QuoVadis Root Certification Authority	\\ DE3F40BD5093D39B6C60F6DABC076201008976C9
8. Comodo	\\ Sectigo (UTN Object)	\\ E12DFB4B41D7D9C32B30514BAC1D81D8385E2D46
9. Comodo	\\ Sectigo (UTN Client)	\\ B172B1A56D95F91FE50287E14D37EA6A4463768A
10. Comodo	\\ Sectigo (AddTrust)	\\ 02FAF3E291435468607857694DF5E45B68851868
11. SK ID Solutions AS	\\ Estonian Certification Centre Root CA	\\ C9A8B9E755805E58E35377A725EBAFC37B27CCD7
12. T-Systems International GmbH (Deutsche Telekom)	\\ Deutsche Telekom Root CA 2	\\ 85A408C09C193E5D51587DCDD61330FD8CDE37BF


This release will **remove the EV policy OID** to the following roots:
1. Google Trust Services (GTS)	\\ Google Trust Services - GlobalSign Root CA-R2	\\ 75E0ABB6138512271C04F85FDDDE38E4B7242EFE
2. Google Trust Services (GTS)	\\ Google Trust Services - GlobalSign ECC Root CA - R4	\\ 6969562E4080F424A1E7199F14BAF3EE58AB6ABB
3. Telia Company (formerly TeliaSonera)	\\ TeliaSonera Root CA v1	\\ 4313BB96F1D5869BC14E6A92F6CFF63469878237



This release will **add the EV SSL OID** to the following roots:
1. WiseKey	\\ OISTE WISeKey Global Root GC CA	\\ E011845E34DEBE8881B99CF61626D1961FC3B931
2. Austrian Society For Data Protection (GlobalTrust)	\\ GLOBALTRUST 2020	\\ D067C11351010CAAD0C76A65373116264F5371A2

This release will **add the Client Authentication, Code Signing, Document Signing, Secure Email, Time Stamping EKU** to the following roots: 
1. Austrian Society For Data Protection (GlobalTrust)	\\ GLOBALTRUST 2020	\\ D067C11351010CAAD0C76A65373116264F5371A2

>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
