---
title: December 2024 Test Environment Deployment Notice - Microsoft Trusted Root Program  
description: This document provides details about the changes made to the test staging platform in December 2024.
ms.date: 12/16/2024
ms.service: security
author: tahminaahmad
ms.author: tahminaahmad
ms.topic: conceptual
---

#  December 2024 Test Environment Deployment Notice - Microsoft Trusted Root Program 
On December 9, 2024, the Microsoft Trusted Root Program updated the test staging platform with root certificates that are planned for a future release. Currently, the new certificates have a Distrust date of November 11, 2024. Once these certificates are tested and incorporated to a future release, the November 11, 2024, date will change to match the date when the new certificates are released.  

The following roots were added as a NotBefore Server Authentication to the test release (CA / Root Certificate / SHA-2 Thumbprint): 
 
Entrust // AffirmTrust 4K TLS Root CA - 2022 // A7DEDF5A842167DD12FDAA0F2080E73295B8B8BEA71B2094EA0950945A482FC1 

Entrust // AffirmTrust Commercial // 0376AB1D54C5F9803CE4B2E201A0EE7EEF7B57B636E8A93C9B8D4860C96F5FA7 

Entrust // AffirmTrust Networking // 0A81EC5A929777F145904AF38D5D509F66B5E2C58FCDB531058B0E17F3F0B41B 

Entrust // AffirmTrust Premium // 70A73F7F376B60074248904534B11482D5BF0E698ECC498DF52577EBF2E93B9A 

Entrust // AffirmTrust Premium ECC // BD71FDF6DA97E4CF62D1647ADD2581B07D79ADF8397EB4ECBA9C5E8488821423 

Entrust // Entrust Root Certification Authority // 73C176434F1BC6D5ADF45B0E76E727287C8DE57616C1E6E6141A2B2CBC7D8E4C 

Entrust // Entrust.net Certification Authority (2048) // 6DC47172E01CBCB0BF62580D895FE2B8AC9AD4F873801E0C10B9C837D21EB177 

Entrust // Entrust 4K EV TLS Root CA - 2022 // 647987D98D52645DA4D3DE3B80771A0CE02B9B9285E6E86999882170744EC9AA 

Entrust // Entrust 4K TLS Root CA - 2022 // DD6C44B39401B053DBE61120748BBB0F6056007665C168E5C286750EDC8DF129 

Entrust // Entrust P384 EV TLS Root CA - 2022 // 937EF8F12276B3C7A3F58E345D09A6EFF01F862F8D2794441CD84D511825FA0C 

Entrust // Entrust P384 TLS Root CA - 2022 // 420332EF876EBE78F2AF5D28AAACDE24AAD0C10F8FFAAC469EFD7BD941929568 

Entrust // Entrust Root Certification Authority - EC1 // 02ED0EB28C14DA45165C566791700D6451D7FB56F0B2AB1D3B8EB070E56EDFF5 

Entrust // Entrust Root Certification Authority - G4 // DB3517D1F6732A2D5AB97C533EC70779EE3270A62FB4AC4238372460E6F01E88 

Entrust // Entrust Root Certification Authority - G2 // 43DF5774B03E7FEF5FE40D931A7BEDF1BB2E6B42738C4E6D3841103D3AA7F339

To test if these changes will affect your systems, please follow the instructions found on: [Testing Instruction - Microsoft Trusted Root Certificate Program](~/Testing.md) . If there are any concerns with impact, please reach out to the Microsoft Root Program as soon as possible through our email at msroot@microsoft.com. 