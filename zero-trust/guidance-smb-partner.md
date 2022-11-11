---
title: Small Business Zero Trust guidance
description: Zero Trust guidance for small and medium-sized business customers and Microsoft partners
search.appverid: MET150 
author: denisebmsft
ms.author: deniseb
manager: dansimp 
audience: Admin
ms.topic: conceptual
ms.date: 11/10/2022
ms.service: microsoft-365-security
ms.subservice: other
ms.localizationpriority:  medium
ms.collection: 
- tier1
- m365-security
- SMB
- m365-initiative-defender-business
ms.custom: intro-overview
ms.reviewer: bcarter
f1.keywords: NOCSH 
---

# Small Business Zero Trust guidance

This article describes Zero Trust deployment guidance and resources for customers and partners working with Microsoft’s small business plans and other technologies commonly used by small business customers.  These resources help you realize the principles of Zero Trust:

- Verify explicitly – authenticate and authorize with identify and device access policies.
- Use least-privilege access – provide users with only the access they need and for the time they need it to perform their tasks.
- Assume breach – do what you can to prevent attacks, protect against threats, and then be ready to respond.

This article also includes information and resources for Microsoft partners.

## Configuration guidance for Microsoft 365 Business Premium

This guidance applies the principles of Zero Trust in an end-to-end configuration process using the capabilities provided in Microsoft Business Premium.

**[Microsoft 365 Business Premium – productivity and cybersecurity for small business](/microsoft-365/business-premium/)**


|Cybersecurity playbook  | Description  |
|---------|---------|
| :::image type="content" source="media/m365bp-cyber-security-playbook.png" alt-text="Screenshot of cybersecurity playbook for small business"::: | In this library: <ul><li>Downloadable poster that guides you through the process of configuring Microsoft 365 Business Premium for Zero Trust.</li><li>Guidance for small and medium-sized businesses who aren’t security experts and need some help getting started</li><li>Steps to secure unmanaged (bring your own device, or BYOD) and managed devices.</li><li>Recommendations and best practices for all employees, including tenant admins, security operations, and all employees.</li></ul> |


| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly  | Multi-factor authentication is turned on by using security defaults. This requires users to register for multi-factor authentication (MFA). It also disables access through legacy authentication (devices that don’t support modern authentication) and requires admins to authenticate every time they sign in. 
For organizations requiring more granular control, guidance is provided for configuring Conditional Access policies. <p>See [Security defaults and multi-factor authentication](/microsoft-365/business-premium/m365bp-conditional-access?view=o365-worldwide).  |
|Row2     |         |

