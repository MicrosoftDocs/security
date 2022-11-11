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
| Verify explicitly  | Multi-factor authentication is turned on by using security defaults. This requires users to register for multi-factor authentication (MFA). It also disables access through legacy authentication (devices that don’t support modern authentication) and requires admins to authenticate every time they sign in. <br/><br/>For organizations requiring more granular control, guidance is provided for configuring Conditional Access policies. <br/><br/>See [Security defaults and multi-factor authentication](/microsoft-365/business-premium/m365bp-conditional-access).  |
| Use least privileged access | Guidance is provided for protecting administrative accounts and not using these accounts for user tasks. <br/><br/>See [Protect your administrator accounts in Microsoft 365 Business Premium](/microsoft-365/business-premium/m365bp-protect-admin-accounts). |
| Assume breach | Protection against malware and other cybersecurity threats is dialed up by using preset security policies. Guidance is provided for training your team to set up unmanaged (bring-your-own-device, or BYOD) devices, use email securely, and collaborate and share more securely. Additional guidance is provided to secure managed devices (devices that your organization owns).<br/><br/>See the following articles:<ul><li>[Review and apply preset security policies](/microsoft-365/business-premium/m365bp-increase-protection)</li><li>[Set up unmanaged (BYOD) devices](/microsoft-365/business-premium/m365bp-devices-overview)</li><li>[Protect all email](/microsoft-365/business-premium/m365bp-protect-email-overview)</li><li>[Collaborate and share securely](/microsoft-365/business-premium/m365bp-collaborate-share-securely)</li><li>[Set up and secure managed devices](/microsoft-365/business-premium/m365bp-protect-devices)</li></ul> |

## Threat protection

This guidance helps protect your organization’s devices, email and collaboration content, and network. 

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | Guidance is provided to help ensure that all devices used to access company data are enrolled in MFA. Recommendations include installing and using Microsoft 365 Apps, such as Outlook, Word, Excel, and PowerPoint, on devices. <br/><br/>See the following articles:<ul><li>[Set up MFA](/microsoft-365/business-premium/m365bp-multifactor-authentication)</li><li>[Install Microsoft 365 Apps](/microsoft-365/business-premium/m365bp-install-office-apps&tabs=iPhone)</li></ul> |
|  Use least privileged access | Guidance is provided for using Microsoft Teams for meetings and collaboration. Recommendations include storing files in Teams and using links to share those files appropriately instead of sending attachments in email. Guidance is provided to adjust the sharing levels in SharePoint and OneDrive to prevent accidental oversharing, and for setting up external users as guests in Microsoft Teams.<br/><br/>See the following articles:<ul><li>[Collaborate and share securely](/microsoft-365/business-premium/m365bp-collaborate-share-securely)</li><li>[Use Microsoft Teams for collaboration](/microsoft-365/business-premium/create-teams-for-collaboration)</li><li>[Set sharing settings for SharePoint and OneDrive files and folders](/microsoft-365/business-premium/m365bp-increase-protection)</li><li>[Manage calendar sharing](/microsoft-365/business-premium/m365bp-increase-protection)</li></ul> |
| Assume breach | Preset security policies for anti-spam, anti-malware, and anti-phishing protection are included. Guidance is provided to increase the level of protection from built-in protection to standard or strict protection. Security admins can also define custom policies to protect devices, email, and documents. When threats are detected, reports, recommendations, and guidance are provided to help review and address threat detections. <br/><br/>See the following articles: <ul><li>[Protect against malware and other cyberthreats with Microsoft 365 Business Premium](/microsoft-365/business-premium/m365bp-increase-protection) </li><li>[Top 10 ways to secure your data](/microsoft-365/admin/security-and-compliance/secure-your-business-data) (for small and medium-sized businesses)</li><li>[Security incident management](/microsoft-365/business-premium/m365bp-security-incident-management) </li></ul> |

## Partner guidance and tools

If you’re a Microsoft partner, you have several options and resources available to help you manage security for your business customers. 

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | The Solutions Partner for Security designation enables customers to identify you as a partner they can trust for integrated security, compliance, and identity solutions. <br/><br/>See [Solutions Partner for Security Learning Path](https://partner.microsoft.com/en-us/training/assets/collection/solutions-partner-for-security#/) (Microsoft Partner Center). |
|  Use least privileged access | Guidance is available to help customers review permissions and administrative access granted to partners. Guidance is also available to help Microsoft Managed Service Providers (MSPs) integrate with their business customers’ tenants. <br/><br/>See the following articles: <ul><li>[Review partner administrative privileges](/microsoft-365/commerce/review-partner-admin-privileges) (guidance for small and medium-sized businesses)</li><li>[Configure MSP integration](/microsoft-365/security/defender-endpoint/configure-mssp-support) </li></ul> |





