---
title: February 2022 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in February 2022 to the root store.
ms.date: 6/3/2022
ms.service: security
author: hasokol-ms
ms.author: hasokol-ms
ms.topic: conceptual
---

# February 2022 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, February 22, 2022, Microsoft released an update to the Microsoft Trusted Root Certificate Program.


This release will **add** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Solutions Notarius Inc	\\ Notarius Root Certificate Authority	\\ B1C3AC0977AAF147E5821A87F8DA32226A210693

This release will **disable** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Athex Exchange S.A. (Athex) \\	ATHEX Root CA G2	\\ 892A1BD4C8B0F8AA9A65ED4CB9D3BF4840B34BC1
2. A-Trust	\\ A-Trust-Qual-02 [CD787]	\\ CD787A3D5CBA8207082848365E9ACDE9683364D8
3. A-Trust	\\ A-Trust-Qual-03a	\\ 42EFDDE6BFF35ED0BAE6ACDD204C50AE86C4F4FA
4. Digicert	\\ Symantec Enterprise Mobile Root for Microsoft	\\ 92B46C76E13054E104F230517E6E504D43AB10B5
5. NLB Nova Ljubljanska Banka d.d. Ljubljana	\\ NLB Nova Ljubljanska Banka d.d. Ljubljana	\\ 0456F23D1E9C43AECB0D807F1C0647551A05F456
6. Pos Digicert Sdn. Bhd (Malaysia)	\\ PosDigicert Class 2 Root CA G2	\\ 313B8D0E7E2E4D20AE8668FFE59DB5193CBF7A32
7. Skaitmeninio sertifikavimo centras (SSC)	\\ SSC GDL CA Root B	\\ C860A318FCF5B7130B1007AD7F614A40FFFF185F
8. Skaitmeninio sertifikavimo centras (SSC)	\\ SSC GDL CA VS Root	\\ D2695E12F592E9C8EE2A4CB8D55E295FEE6B2D31
9. Swiss BIT, Swiss Federal Office of Information Technology, Systems and Telecommunication (FOITT)	\\ Swiss Government Root CA II	\\ C7F7CBE2023666F986025D4A3E313F29EB0C5B38
10. Swiss BIT, Swiss Federal Office of Information Technology, Systems and Telecommunication (FOITT) \\	Swiss Government Root CA III	\\ CCEAE32445CD4218DD188EADCEB3133C7FB340AD


This release will **NotBefore** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Certinomis / Docapost	\\ Certinomis - Root CA	\\ 9D70BB01A5A4A018112EF71C01B932C534E788A8
2. Cisco	\\ Cisco Systems	\\ DE990CED99E0431F60EDC3937E7CD5BF0ED9E5FA


This release will **NotBefore Code Signing EKU** for the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. NetLock Ltd.	\\ NetLock Arany (Class Gold) Fotanusitvany	\\ 06083F593F15A104A069A46BA903D006B7970991


This release will **NotBefore Server Authentication EKU** for the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Swiss BIT, Swiss Federal Office of Information Technology, Systems and Telecommunication (FOITT)	\\ Swiss Government Root CA I	\\ A1585187156586CEF9C454E22AB15C58745607B4


This release will **remove** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Cisco	\\ RXC-R2	\\ 2C8AFFCE966430BA04C04F81DD4B49C71B5B81A0
2. Comodo	\\ Sectigo (UTN Hardware)	\\ 0483ED3399AC3608058722EDBC5E4600E3BEF9D7
3. Cybertrust Japan / JCSI	\\ Japan Certification Services, Inc. SecureSign RootCA3	\\ 8EB03FC3CF7BB292866268B751223DB5103405CB
4. Cybertrust Japan / JCSI	\\ Japan Certification Services, Inc. SecureSign RootCA1	\\ CABB51672400588E6419F1D40878D0403AA20264
5. TurkTrust	\\ TURKTRUST Elektronik Sertifika Hizmet Saglayicisi H6	\\ 8A5C8CEEA503E60556BAD81BD4F6C9B0EDE52FE0



>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
