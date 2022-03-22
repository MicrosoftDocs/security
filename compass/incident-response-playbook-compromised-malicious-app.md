---
title: Compromised and malicious applications
description: Learn how to investigate if one or more applications in a customer tenant are compromised.
keywords: compromise, malicious, applications, investigation, attack, microsoft threat protection, microsoft 365, search, query, telemetry, security events, antivirus, firewall, incident response, playbook, guidance, Microsoft 365 Defender
search.product: DART
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
  - NOCSH
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: 
  - M365-security-compliance
  - m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
---

# Compromised and malicious applications

This article provides guidance on identifying and investigating malicious attacks on one or more applications in a customer tenant that are compromised. The step-by-step instructions will help you take the required remedial action to protect information and minimize further risks.

- **Prerequisites:** Covers the specific requirements you need to complete before starting the investigation. For example, logging that should be turned on, roles and permissions required, among others.
- **Workflow:** Shows the logical flow that you should follow to perform this investigation.
- **Investigation steps:** Includes a detailed step-by-step guidance for this specific investigation.
- **Recovery steps:** Contains high-level steps on how to recover/mitigate from a malicious attack on compromised applications.
- **References:** Contains additional reading and reference materials.

## Prerequisites

Before starting the investigation, make sure you have detailed information on the applications that you suspect to be compromised by the malicious attack.

- To leverage Identity protection signals, the tenant must be licensed for P2
  - Understanding of the [Identity Protection risk concepts](/azure/active-directory/identity-protection/concept-identity-protection-risks)
  - Understanding of the [Identity protection investigation concepts](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk)

- Ability to use Graph Explorer and be familiar (to some extend) with the Microsoft Graph API

- An account with the following directory roles:
  - Global administrator
  - Security administrator

- Familiarize yourself with the [application auditing concepts](/azure/active-directory/fundamentals/security-operations-applications) (part of https://aka.ms/AzureADSecOps)

- Make sure application owners have the set of ALL Enterprise apps in your tenant. Review the concepts [here](/azure/active-directory/manage-apps/overview-assign-app-owners) and [here](/azure/active-directory/manage-apps/assign-app-owners).

- Familiarize yourself with the concepts of the [App Consent grant investigation](/security/compass/incident-response-playbook-app-consent) (part of https://aka.ms/IRPlaybooks)

- Make sure you understand the following Azure AD permissions: 
  - [Risky permissions](/security/compass/incident-response-playbook-app-consent#classifying-risky-permissions)
  - [Consent model and the Admin consent workflow](/azure/active-directory/manage-apps/configure-admin-consent-workflow)

### Required tools

For an effective investigation, install the following PowerShell module and the toolkit on your investigation machine:

- [Azure AD Incident Response PowerShell Module](https://github.com/AzureAD/Azure-AD-Incident-Response-PowerShell-Module)
- [Azure AD Toolkit](https://github.com/microsoft/AzureADToolkit)

## Workflow