---
title: August 2021 Deployment Notice - Microsoft Trusted Root Program 
description: This document provides details about the changes made in August 2021 to the root store.
ms.date: 6/3/2022
ms.service: security
author: hasokol
ms.author: hasokol
ms.topic: conceptual
---

# August 2021 Deployment Notice - Microsoft Trusted Root Program 

On Tuesday, August 24, 2021, Microsoft released an update to the Microsoft Trusted Root Certificate Program.

This release will **disable** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. DocuSign (OpenTrust/Keynectis)	\\ KEYNECTSIS ROOT CA	\\ 9C615C4D4D85103A5326C24DBAEAE4A2D2D5CC97
2. Autoridad de Certificacion (ANF AC)	\\ ANF Global Root CA	\\ 5BB59920D11B391479463ADD5100DB1D52F43AD4
3. Autoridad de Certificacion (ANF AC)	\\ ANF AC	\\ CEA9890D85D80753A626286CDAD78CB566D70CF2
4. Government of Lithuania, Registru Centras	\\ VI Registru Centras RCSC (RootCA)	\\ 971D3486FC1E8E6315F7C6F2E12967C724342214
5. Government of Spain, Fabrica Nacional de Moneda y Timbre (FNMT)	\\ AC RAIZ FNMT-RCM (B8651)	\\ B865130BEDCA38D27F69929420770BED86EFBC10
6. Japan Local Authority Information Systems (J-LIS)	\\ Application CA G3 Root	\\ 6F3884568E99C8C6AC0E5DDE2DB202DD002E3663
7. NetLock Ltd.	\\ NetLock Kozjegyzoi (Class A) Tanusitvanykiado	\\ ACED5F6553FD25CE015F1F7A483B6A749F6178C6
8. Red Abogacia	\\ Autoridad de Certificacion de la Abogacia	\\ 7F8A77836BDC6D068F8B0737FCC5725413068CA4
9. Shanghai Electronic Certification Authority Co., Ltd. (SHECA)	\\ UCA Root	\\ 8250BED5A214433A66377CBC10EF83F669DA3A67
10. Shanghai Electronic Certification Authority Co., Ltd. (SHECA)	\\ UCA Global Root	\\ 0B972C9EA6E7CC58D93B20BF71EC412E7209FABF
11. SSL.com	\\ SSL.com EV Root Certification Authority RSA	\\ 1CB7EDE176BCDFEF0C866F46FBF980E901E5CE35
12. Skaitmeninio sertifikavimo centras (SSC)	\\ SSC GDL CA Root A	\\ 0C2009A4A88D8B4202185250540CC42BDFB5B089
13. Government of France (ANSSI, DCSSI)	\\ IGC/A AC racine Etat francais	\\ 1AC92F09EA89E28B126DFAC51E3AF7EA9095A3EE
14. Personal I.D. Ltd	\\ PersonalID Trustworthy RootCA 2011	\\ 4394CE3126FF1A224CDD4DEEB4F4EC1DA368EF6A
15. Halcom D.D.	\\ Halcom Root CA	\\ 535B001672ABBF7B6CC25405AE4D24FE033FD1CC
16. Government of France (ANSSI, DCSSI)	\\ Secretariat General de la Defense Nationale	\\ 60D68974B5C2659E8A0FC1887C88D246691B182C
17. Swisscom (Switzerland) Ltd	\\ Swisscom Root CA 2	\\ 77474FC630E40F4C47643F84BAB8C6954A8A41EC
18. Government of Australia	Australian Defence Organisation (ADO) Certificate Authority 02	\\ 84429D9FE2E73A0DC8AA0AE0A902F2749933FE02
19. SwissSign AG	\\ SwissSign Silver Root CA – G3	\\ 8D08FC43C0770CA84F4DCCB2D41A5D956D786DC4
20. Image-X Enterprises Inc	\\ ESIGNIT.ORG	\\ 9F8DE799CF8764ED2466990564041B194919EDE8
21. Orange Polska S.A.	\\ Signet Root CA	\\ B2BD9031AA6D0E14F4C57FD548258F37B1FB39E4
22. TurkTrust	\\ TURKTRUST Elektronik Sertifika Hizmet SaÄŸlayÄ±cÄ±sÄ± H5	\\ C418F64D46D1DF003D2730137243A91211C675FB
23. LuxTrust	\\ LuxTrust Global Root CA	\\ C93C34EA90D9130C0F03004B98BD8B3570915611
24. Microsoft Corporation	\\ Microsoft Root Certificate Authority	\\ CDD4EEAE6000AC7F40C3802C171E30148030C072
25. Athex Exchange S.A. (Athex)	\\ Athex Root CA	\\ DB2B7B434DFB7FC1CB5926EC5D9521FE350FF279
26. Government of Japan, Ministry of Internal Affairs and Communications	\\ GPKI ApplicationCA2 Root	\\ F00FC37D6A1C9261FB6BC1C218498C5AA4DC51FB
27. Digidentity BV **	\\ Digidentity BV	\\ F138A330A4EA986BEB520BB11035876EFB9D7F1C


This release will **disallow the Server Authentication EKU** to the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Government of Saudi Arabia, NCDC	\\ Saudi National Root CA	\\ 8351509B7DF8CFE87BAE62AEB9B03A52F4E62C79
2. Agencia Notarial de Certificacion (ANCERT)	\\ ANCERT Certificados CGN V2	\\ 7EB1A0429BE5F428AC2B93971D7C8448A536070C


This release will **NotBefore** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Telia Company (formerly TeliaSonera)	\\ Sonera Class2 CA	\\ 37F76DE6077C90C5B13E931AB74110B4F2E49A27
2. Netrust	\\ Netrust CA1	\\ 55C86F7414AC8BDD6814F4D86AF15F3710E104D0
3. Government of The Netherlands, PKIoverheid (Logius)	\\ Staat der Nederlanden Root CA - G2	\\ 59AF82799186C7B47507CBCF035746EB04DDB716
4. NetLock Ltd.	\\ NetLock Minositett Kozjegyzoi (Class QA) Tanusitvanykiado	\\ 016897E1A0B8F2C3B134665C20A727B7A158E28F
5. Collegio de Registradores Mercantile (Spanish Property & Commerce Registry)	\\ Colegio de Registradores Mercantiles	\\ 211165CA379FBB5ED801E31C430A62AAC109BCB4
6. Trustis	\\ Trustis FPS Root CA	\\ 3BC0380B33C3F6A60C86152293D9DFF54B81C004
7. Government of Tunisia, Agence National de Certification Electronique / National Digital Certification Agency (ANCE/NDCA)	\\ Tunisian Root Certificate Authority - TunRootCA2	\\ 9638633C9056AE8814A065D23BDC60A0EE702FA7
8. Government of Spain, Direccion General de la Policia, Ministerio del Interior, Espana.	\\ DIRECCION GENERAL DE LA POLICIA	\\ B38FECEC0B148AA686C3D00F01ECC8848E8085EB


This release will **NotBefore the Code Sign EKU** to the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Entrust	\\ Entrust Root Certification Authority - G4	\\ 14884E862637B026AF59625C4077EC3529BA9601
2. QuoVadis	\\ QuoVadis Root CA 1 G3	\\ 1B8EEA5796291AC939EAB80A811A7373C0937967
3. GlobalSign	\\ GlobalSign ECC Root CA - R5	\\ 1F24C630CDA418EF2069FFAD4FDD5F463A1B69AA
4. QuoVadis	\\ QuoVadis Root CA 3	\\ 1F4914F7D874951DDDAE02C0BEFD3A2D82755185
5. Entrust	\\ Entrust Root Certification Authority - EC1	\\ 20D80640DF9B25F512253A11EAF7598AEB14B547
6. SECOM Trust Systems CO. LTD.	\\ SECOM Trust Systems CO LTD [36B12]	\\ 36B12B49F9819ED74C9EBC380FC6568F5DACB2F7
7. Trustwave	\\ Trustwave [3A44]	\\ 3A44735AE581901F248661461E3B9CC45FF53A1B
8. QuoVadis	\\ QuoVadis Root CA 3 G3	\\ 4812BD923CA8C43906E7306D2796E6A4CF222E7D
9. EDICOM	\\ CAEDICOM ROOT	\\ 559BBA7B0FFE80D6D3829B1FD07AA4D322194790
10. Amazon	\\ Amazon Root CA 2	\\ 5A8CEF45D7A69859767A8C8B4496B578CF474B1A
11. Digicert	\\ Cybertrust Global Root	\\ 5F43E5B1BFF8788CAC1CC7CA4A9AC6222BCC34C6
12. GlobalSign	\\ GlobalSign Root CA - R6	\\ 8094640EB5A7A1CA119C1FDDD59F810263A7FBD1
13. Digicert	\\ DigiCert Global Root CA	\\ 912198EEF23DCAC40939312FEE97DD560BAE49B1
14. Amazon	\\ Amazon Services Root Certificate Authority -- G2	\\ 925A8F8D2C6D04E0665F596AFF22D863E8256F3F
15. SwissSign AG	\\ SwissSign Silver G2 Root CA	\\ 9BAAE59F56EE21CB435ABE2593DFA7F040D11DCB
16. Digicert	\\ DigiCert	\\ A8985D3A65E5E5C4B2D7D66D40C6DD2FB19C5436
17. Trustwave	\\ Trustwave [B8018]	\\ B80186D1EB9C86A54104CF3054F34C52B7E558C6
18. SwissSign AG	\\ SwissSign	\\ D8C5388AB7301B1B6ED47AE645253A6F9F1A2761
19. Digicert	\\ DigiCert Global Root G2	\\ DF3C24F9BFD666761B268073FE06D1CC8D4F82A4
20. NetLock Ltd.	\\ NetLock Platina (Class Platinum) Fotanusitvany	\\ EC93DE083C93D933A986B3D5CDE25ACB2FEECF8E
21. Digicert	\\ DigiCert Assured ID Root G3	\\ F517A24F9A48C6C9F8A200269FDC0F482CAB3089
22. Amazon	\\ Amazon Root CA 4	\\ F6108407D6F8BB67980CC2E244C2EBAE1CEF63BE
23. HARICA	\\ Hellenic Academic and Research Institutions RootCA 2011	\\ FE45659B79035B98A161B5512EACDA580948224D
24. MULTICERT	\\ MULTICERT Root Certification Authority 01	\\ 46AF7A31B599460D469D6041145B13651DF9170A

This release will **NotBefore Server Authentication EKU** the following roots (CA \ Root Certificate \ SHA-1 Thumbprint):
1. Chunghwa Telecom	\\ Chunghwa Telecom Co. Ltd.	\\ 67650DF17E8E7E5B8240A4F4564BCFE23D69C6F0
2. Chunghwa Telecom	\\ ePKI Root Certification Authority - G2 [D99B1]	\\ D99B104298594763F0B9A927B79269CB47DD158B


>[!NOTE]
> * As part of this release, Microsoft also updated the Untrusted CTL time stamp and sequence number. No changes were made to the contents of the Untrusted CTL but this will cause your system to download/refresh the Untrusted CTL. This is a normal update that is sometimes done when the Trusted Root CTL is updated.
> * The update package will be available for download and testing at: <https://aka.ms/CTLDownload>
> * Signatures on the Certificate Trust Lists (CTLs) for the Microsoft Trusted Root Program changed from dual-signed (SHA-1/SHA-2) to SHA-2 only. No customer action required. For more information, please visit: <https://support.microsoft.com/en-us/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus>
