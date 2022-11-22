---
title: Small business Zero Trust guidance
description: Zero Trust guidance for small and medium-sized business customers and Microsoft partners
search.appverid: MET150 
author: denisebmsft
ms.author: deniseb
manager: dansimp 
audience: Admin
ms.topic: conceptual
ms.date: 11/22/2022
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

# Small business Zero Trust guidance

This article describes Zero Trust deployment guidance and resources for customers and partners working with Microsoft 365 for business and other technologies commonly used by small- to medium-sized business customers.  These resources help you realize the principles of Zero Trust:

- **Verify explicitly** – authenticate and authorize with identify and device access policies.
- **Use least-privilege access** – provide users with only the access they need and for the time they need it to perform their tasks.
- **Assume breach** – do what you can to prevent attacks, protect against threats, and then be ready to respond.

This article also includes information and resources for Microsoft partners.

## Configuration guidance for Microsoft 365 Business Premium

Microsoft 365 Business Premium is a comprehensive cloud productivity and security solution designed especially for small and medium sized businesses. This guidance applies the principles of Zero Trust in an end-to-end configuration process using the capabilities provided in Microsoft 365 Business Premium.

**[Microsoft 365 Business Premium – productivity and cybersecurity for small business](/microsoft-365/business-premium/)**


|Cybersecurity playbook  | Description  |
|---------|---------|
| :::image type="content" source="media/m365bp-cyber-security-playbook.png" alt-text="Screenshot of cybersecurity playbook for small business"::: | In this library: <ul><li>Downloadable poster that guides you through the process of configuring Microsoft 365 Business Premium for Zero Trust.</li><li>Guidance for small and medium-sized businesses who aren’t security experts and need some help getting started.</li><li>Steps to secure unmanaged (bring your own device, or BYOD) and managed devices.</li><li>Recommendations and best practices for all employees, including tenant admins, security operations, and all employees.</li></ul> |

See the following resources:

- [Microsoft 365 Business Premium - Productivity and cybersecurity for small business](/microsoft-365/business-premium/)
- [Cybersecurity playbook for Microsoft 365 Business Premium](/microsoft-365/business-premium/)
- [Microsoft 365 Business Premium resources for partners and small business](/microsoft-365/business/)

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly  | Multi-factor authentication (MFA) is turned on by using security defaults (or Conditional Access). This configuration requires users to register for MFA. It also disables access through legacy authentication (devices that don’t support modern authentication) and requires admins to authenticate every time they sign in.  |
| Use least privileged access | Guidance is provided for protecting administrative accounts and not using these accounts for user tasks. |
| Assume breach | Protection against malware and other cybersecurity threats is dialed up by using preset security policies. Guidance is provided for training your team to set up unmanaged (bring-your-own-device, or BYOD) devices, use email securely, and collaborate and share more securely. Additional guidance is provided to secure managed devices (devices that your organization owns).  |

## Additional threat protection

Microsoft 365 Business Premium includes Microsoft Defender for Business, which provides comprehensive security for devices with a simplified configuration experience. Optimized for small and medium-sized businesses, capabilities include threat & vulnerability management, next-generation protection (antivirus and firewall), automated investigation & remediation, and more.

Microsoft 365 Business Premium also includes advanced anti-phishing, anti-spam, and anti-malware protection for email content and Office files (Safe Links and Safe Attachments) with Microsoft Defender for Office 365 Plan 1. With these capabilities, your email and collaboration content is more secure and better protected.

See the following resources:

- [What is Microsoft Defender for Business?](/microsoft-365/security/defender-business/mdb-overview)
- [Microsoft Defender for Office 365 Plan 1](/microsoft-365/security/office-365-security/microsoft-defender-for-office-365-product-overview#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)


| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | Devices that access company data must meet security requirements. |
|  Use least privileged access | Guidance is provided for using roles to assign permissions and security policies to prevent unauthorized access. |
| Assume breach | Advanced protection is provided for devices, email, and collaboration content. Remediation actions are taken when threats are detected. |

## Partner guidance and tools

If you’re a Microsoft partner, several resources are available to help you manage security for your business customers. These resources include learning paths, guidance, and integration.

The Solutions Partner for Security designation enables customers to identify you as a partner they can trust for integrated security, compliance, and identity solutions. See [Solutions Partner for Security Learning Path (Microsoft Partner Center)](https://partner.microsoft.com/training/assets/collection/solutions-partner-for-security#/).

Guidance is available to help customers review permissions and administrative access granted to partners. Guidance is also available to help Microsoft Managed Service Providers (MSPs) integrate with their business customers’ tenants. See the following articles: 

- [Review partner administrative privileges](/microsoft-365/commerce/review-partner-admin-privileges) 
- [Configure MSP integration](/microsoft-365/security/defender-endpoint/configure-mssp-support)

Resources are available to help you as a Microsoft partner to manage your customers’ security settings, and to help protect their devices and data. Microsoft 365 Lighthouse integrates with [Microsoft 365 Business Premium](/microsoft-365/business-premium/), [Microsoft Defender for Business](/microsoft-365/security/defender-business/mdb-overview), and [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/). The Defender for Endpoint APIs can be used to integrate device security capabilities in Microsoft 365 Business Premium with remote monitoring and management (RMM) tools and professional service automation (PSA) software. See the following articles:

- [Integrate Microsoft endpoint security with your RMM tools and PSA software](/microsoft-365/security/defender-business/mdb-partners#integrate-microsoft-endpoint-security-with-your-rmm-tools-and-psa-software)
- [Use Microsoft 365 Lighthouse to secure and manage your customers’ devices and data](/microsoft-365/security/defender-business/mdb-partners#use-microsoft-365-lighthouse-to-secure-and-manage-your-customers-devices-and-data)
- [Help for partners (general information and support)](https://support.microsoft.com/topic/help-for-partners-ae811622-b838-4f62-b7e9-659627374963)

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | Partner resources are available to help Microsoft partners configure and manage their customers’ identity and access methods and policies. |
|  Use least privileged access | Partners can configure integration with customer tenants. Customers can review permissions and administrative access granted to partners. |
| Assume breach | Microsoft 365 Lighthouse integrates with Microsoft threat protection capabilities for small and medium-sized businesses. |

## Protect other SaaS apps you or your customers use

You or your small business customers likely use other Software as a Service (SaaS) applications, like Salesforce, Adobe Creative Cloud, and DocuSign. You can integrate these applications with Azure Active Directory (Azure AD) and include these in your multi-factor authentication and conditional access policies. 

The Azure AD application gallery is a collection of software as a service (SaaS) applications that have been pre-integrated with Azure AD. All you need to do is find the application in the gallery and add it to your environment. Then, the application will be available for you to include in the scope of your multi-factor authentication and conditional access rules. See [Overview of the Azure AD application gallery](/azure/active-directory/manage-apps/overview-application-gallery).

After you add SaaS apps to your environment, these apps will automatically be protected with Azure AD Multi-Factor Authentication and the other protections provided by security defaults. If you're using Conditional Access policies instead of security defaults, you need to add these apps to the scope of your Conditional Access and related policies. See [Security defaults and multi-factor authentication](/microsoft-365/business-premium/m365bp-conditional-access).

Azure AD determines when a user will be prompted for Azure AD Multi-Factor Authentication based on factors such as location, device, role, and task. This functionality protects all applications registered with Azure AD, including SaaS applications. See [Providing a default level of security in Azure Active Directory](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults#require-users-to-do-multifactor-authentication-when-necessary).

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | All SaaS apps you add require multi-factor authentication for access. |
| Use least privileged access | Users must meet authentication requirements to use apps that access company data. |
| Assume breach | Factors, such as location, device, role, and task are considered when users are authenticated. Multi-factor authentication is used when necessary. |

