---
title: Upcoming Changes Backlog - Microsoft Trusted Root Certificate Program
description: This document provides details about the changes made monthly to the root store.
ms.date: 03/04/2019
ms.service: security
ms.author: kasirota
ms.topic: conceptual
---

# Upcoming Changes Backlog - Microsoft Trusted Root Certificate Program

The Microsoft Trusted Root Certificate Program releases changes to our Root Store on a monthly cadence, except for December. The public can expect the following cadence for releases: 
1.	Additions and non-deprecating modifications will be completed any month
2.	Certificate Authority (CA)-initiated and CA-confirmed deprecations will occur on even numbered months
3.	Microsoft-initiated deprecations will occur in February and August releases

Changes to the CTL are generally pushed at the end of the month listed in the release column. However, NotBefore and Disable dates are set on the first of the month to allow for accurate testing.
 
 
 > [!NOTE]
 > If a release is listed as TBD, it has not yet been scheduled. If there is a month in the release column, the change has been scheduled. Confirmed changes can also be found with the release notes at <http://aka.ms/rootupdates>. 
 > Modifications to scheduled releases can only be guaranteed until the 10th of the month of release. We will try to accomodate for modifications requested after that date.


Please note, the changes listed are accurate at the time of posting but are subject to change. This list is updated every Monday. 

If you are a certificate user who has active certificates chaining up to a deprecating root,  please reach out to your CA to understand how changes may impact your certificates. 

Update packages will be available for download and testing at <https://aka.ms/CTLDownload> 

## CA-Requested Root Changes 
These are changes that have been requested by the CA or the CA has confirmed with Microsoft that the changes proposed are approved by the CA. 

| Release |	CA Name 	| Root Name | Root Thumbprint | Type of Change | Notes | 
|---|---|---|---|---|---|
| September 2019 | A-Trust | XX | XX | Add |  |
| October 2019 | A-Trust | A-Trust-nQual-03 | 4CAEE38931D19AE73B31AA75CA33D621290FA75E | NotBefore |  |
| October 2019 | A-Trust | A-Trust-Qual-02 | CD787A3D5CBA8207082848365E9ACDE9683364D8 | NotBefore |  |
| October 2019 | A-Trust | A-Trust-Qual-02 | 42EFDDE6BFF35ED0BAE6ACDD204C50AE86C4F4FA | NotBefore |  |
| October 2019 | A-Trust | A-Trust-Root-05 | 2E66C9841181C08FB1DFABD4FF8D5CC72BE08F02 | NotBefore |  |



## Microsoft-initiated Root Changes 

The reason this action will be taken is listed in the table. If there are any concerns, please send an email to msroot@microsoft.com as soon as possible. 

| Release |	CA Name 	| Root Name | Root Thumbprint | Type of Change | Reason for deprecation | 
|---|---|---|---|---|---|
| February 2020 | Skaitmeninio sertifikavimo centras (SSC) | SSC GDL CA Root B | C860A318FCF5B7130B1007AD7F614A40FFFF185F | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | Skaitmeninio sertifikavimo centras (SSC) | SSC GDL CA VS Root | D2695E12F592E9C8EE2A4CB8D55E295FEE6B2D31 | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | Post of Slovenia | POSTarCA | B1EAC3E5B82476E9D50B1EC67D2CC11E12E0B491 | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | Post of Serbia | Posta CA Root | D6BF7994F42BE5FA29DA0BD7587B591F47A44F22 | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | NLB Nova Ljubljanska Banka d.d. Ljubljana | NLB Nova Ljubljanska Banka d.d. Ljubljana | 0456F23D1E9C43AECB0D807F1C0647551A05F456 | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | China Financial Certification Authority (CFCA) | China Financial CA | EABDA240440ABBD694930A01D09764C6C2D77966 | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | China Internet Network Information Center (CNNIC) | China Internet Network Information Center EV Certificates Root | 4F99AA93FB2BD13726A1994ACE7FF005F2935D1E | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | China Internet Network Information Center (CNNIC) | CNNIC Root | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F | NotBefore | Audits > 1 old on CCADB. |
| February 2020 | China Internet Network Information Center (CNNIC) | CNNIC Root | 8BAF4C9B1DF02A92F7DA128EB91BACF498604B6F | NotBefore | Audits > 1 old on CCADB. |
