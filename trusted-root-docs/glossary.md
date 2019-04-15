---
title: Glossary - Microsoft Trusted Root Certificate Program
description: This document provides details about the changes made monthly to the root store.
ms.date: 03/04/2019
ms.service: security
ms.author: kasirota
ms.topic: conceptual
---

# Glossary of changes - Microsoft Trusted Root Certificate Program

Below are listed the different changes that Microsoft Trusted Root Program can make at any given time.

First of the release month date refers to the 1st day of the month the release is scheduled in. For example, if a change is scheduled for the April release, first of the release month date is April 1st. The release date will be day the changes are pushed, which is generally the last Tuesday of the Month. 

## Action: NotBefore the Server Authentication EKU only
Definition of action: This root will no longer be able to issue TLS certificates that will be trusted. Any certificates issued before the first of the release month NotBefore date will continue to be trusted. All other EKUs will be unaffected. 


## Action: Disable
Definition of action: All existing certs, with the exception of code-signing and time-stamping certs, will no longer be trusted. Code-signing and time-stamping certificates will no longer be able to issue code-sign or time-stamp code that will be trusted. Anything that is signed after the April 1st disable date will be seen as revoked. Code that has been signed or timestamps issued before the April 1st disable date will continue to function. 
