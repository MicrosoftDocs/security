---
title: April 2019 Deployment Notice (15/March) - Microsoft Trusted Root Program 
description: This document provides details about the changes made in March 2019 to the root store.
ms.date: 04/15/2019
ms.service: security
ms.author: kasirota
ms.topic: conceptual
---

# April 2019 Deployment Notice (15/April) - Microsoft Trusted Root Program 

On Tuesday, April 30th, 2019, Microsoft will release a planned update to the Microsoft Trusted Root Certificate Program.

This release will **add** the following roots (Root Certificate \\ SHA-1 Thumbprint):

1.  Trustwave Global Certification Authority \\	2F8F364FE1589744215987A52A9AD06995267FB5
2.  Trustwave Global ECC P256 Certification Authority \\ 	B49082DD450CBE8B5BB166D3E2A40826CDED42CF
3.  Trustwave Global ECC P384 Certification Authority \\ 	E7F3A3C8CF6FC3042E6D0E6732C59E68950D5ED2
4.  VRK Gov Root CA - G2 \\ F435F85F0108DA684E7BFD517C90C627BB9A6CF5 

This release will **Disable** the following roots:

1.  S-TRUST Authentication and Encryption Root CA 2005:PN \\ BEB5A995746B9EDF738B56E6DF437A77BE106B81
2.  Halcom CA PO 2 \\ 7FBB6ACD7E0AB438DAAF6FD50210D007C6C0829C
3.  I.CA – Qualified Certification Authority \\ D2441AA8C203AECAA96E501F124D52B68FE4C375
4.  I.CA – Standard Certification Authority \\ 90DECE77F8C825340E62EBD635E1BE20CF7327DD
5.  ComSign CA \\ E1A45B141A21DA1A79F41A42A961D669CD0634C1
6.  ComSign Secured CA \\ F9CD0E2CDA7624C18FBDF0F0ABB645B8F7FED57A
7.  CA Disig Root R1 \\ 8E1C74F8A620B9E58AF461FAEC2B4756511A52C6

This release will **NotBefore** the following roots:

1.  SwissSign Gold Root CA – G3 \\ 0B7199A1C7F3ADDF7BA7EAB8EB574AE80D60DDDE
2.  SwissSign Silver Root CA – G3 \\ 8D08FC43C0770CA84F4DCCB2D41A5D956D786DC4
3.  SwissSign Platinum Root CA – G3 \\ 	A1E7C600AA4170E5B74BC94F9B9703EDC261B4B9
4.  AC Raíz Certicámara S.A \\ CBA1C5F8B0E35EB8B94512D3F934A2E90610D336

This release will **NotBefore the code signing EKU** in the following roots:

1.  TWCA Global Root CA \\ 9CBB4853F6A4F6D352A4E83252556013F5ADAF65
2.  Macao Post eSign Trust \\ 06143151E02B45DDBADD5D8E56530DAAE328CF90

This release will **NotBefore the server authentication EKU** in the following roots:

1. SwissSign Platinum G2 Root CA \\ 56E0FAC03B8F18235518E5D311CAE8C24331AB66

>[!NOTE]
> * Windows 10 allows us to stop trusting roots or EKU's using the "NotBefore" or "Disable" properties, both of which allow us to remove certain capabilities of the root certificate without complete removal. These features are not available on versions prior to Windows 10. Earlier versions of Windows will be unaffected by this change. 

> * The NotBefore and Disable dates are set for the first day of the release month. This means that all certificates issued after April 1st will be affected.  

> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
