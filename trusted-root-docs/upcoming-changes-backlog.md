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

Changes to the CTL are generally pushed at the end of the month listed. However, NotBefore and Disable dates are set on the first of the month to allow for accurate testing.

If a release is listed as TBD, it has not yet been scheduled. If there is a month in the release column, the change has been scheduled. 
Confirmed changes can also be found with the release notes here <http://aka.ms/rootupdates>. 

Please note, the changes listed are accurate at the time of posting but are subject to change. If you are a certificate user who has active certificates chaining up to a deprecating root,  please reach out to your CA to understand how changes may impact your certificates. 
Update packages will be available for download and testing at <https://aka.ms/CTLDownload> 

## CA-Requested and CA-Confirmed Root Changes 


| Release |	CA Name 	| Root Name | Root Thumbprint | Type of Change | Notes | 
|---|---|---|---|---|---|
| April | KarinaCA | Karina Root | 111111111111111111111 | NotBefore |  |
| TBD | KarinaCA | Karina Root | 111111111111111111111 | Add |  |


## Microsoft-initiated Root Changes 

The reason this action will be taken is listed in the table. If there are any concerns, please send an email to msroot@microsoft.com as soon as possible. 

| Release |	CA Name 	| Root Name | Root Thumbprint | Type of Change | Reason for deprecation | 
|---|---|---|---|---|---|
| August | KarinaCA | Karina Root | 111111111111111111111 | NotBefore | Audits > 1 old on CCADB. |


## Pending applications

This queue is listed in order of application. 

| Release |	Certificate Authority Name 	| Root Name | Root Thumbprint | Notes |
|---|---|---|---|---|
| TBD | KarinaCA | Karina Root | 111111111111111111111 | NotBefore |  |
| TBD | KarinaCA | Karina Root | 111111111111111111111 | Add |  |

