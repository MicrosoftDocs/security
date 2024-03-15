---
title: Deprecation Actions  - Microsoft Trusted Root Certificate Program
description: Get to know the changes made monthly to the root store.
ms.date: 02/14/2024
ms.service: security
author: kasirota
ms.author: kasirota
ms.topic: conceptual
---

# Deprecation Definitions - Microsoft Trusted Root Certificate Program

Windows has many options for deprecating root certificate capbilities. These capabilities are listed here. 

## Removal
Removal of a root from the CTL.  All certificates that chain to the root are no longer trusted. Users can still manually install the root into the Local Machine “Trusted Root Certification Authorities”/Registry physical store. However, if installed into the Local Machine “Trusted Root Certification Authorities”/Third-Party physical store, will be auto deleted by the auto root update service.
 
## EKU Removal

Removal of a specific EKU from a root certificate. All End entity certificates that chain to this root can no longer utilize the removed EKU, independent of whether or not the digital signature was timestamped. 

## Disallow

This feature involves adding the certificate to the Disallow CTL and can be used to revoke many types of certificates such as self-signed certificates, enterprise certificates, trusted root certificates, or high risk leaf certificates.  This feature effectively revokes the certificate. Users cannot manually install the root and continue to have trust.

## Disable

All certificates that chain to a disabled root will no longer be trusted with a very important exception; digital signatures with a timestamp prior to the disable date will continue to validate successfully.

## NotBefore	

Allows granular disabling of a root certificate or specific EKU capability of a root certificate.  Certificates issued AFTER the NotBefore date will no longer be trusted, however certificates issued BEFORE to the NotBefore date will continue to be trusted. Digital signatures with a timestamp set before the NotBefore date will continue to successfully validate.
