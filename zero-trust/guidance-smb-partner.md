---
title: Small business Zero Trust guidance
description: Zero Trust guidance for small and medium-sized business customers and Microsoft partners.
search.appverid: MET150 
author: denisebmsft
ms.author: deniseb
manager: dansimp 
audience: Admin
ms.topic: conceptual
ms.date: 01/08/2024
ms.service: microsoft-365-security
ms.subservice: other
ms.localizationpriority:  medium
ms.collection: 
- tier1
- m365-security
- SMB
- m365-initiative-defender-business
- zerotrust-smb
- m365solution-zero-trust
ms.custom: intro-overview
ms.reviewer: bcarter
f1.keywords: NOCSH 
---

# Small business Zero Trust guidance

This article describes Zero Trust deployment guidance and resources for customers and partners working with Microsoft 365 Business Premium and other technologies commonly used by small- to medium-sized business customers. These resources help you realize the principles of Zero Trust:


| Verify explicitly | Use least privilege access | Assume breach |
|------|-------|------|
| Always authenticate and authorize with identity and device access policies. | Provide users with only the access they need and for the time they need it to perform their tasks. | Do what you can to prevent attacks, protect against threats, and then be ready to respond. |

This article also includes information and resources for Microsoft partners.

## Configuration guidance for Microsoft 365 Business Premium

Microsoft 365 Business Premium is a comprehensive cloud productivity and security solution designed especially for small and medium sized businesses. This guidance applies the principles of Zero Trust in an end-to-end configuration process using the capabilities provided in Microsoft 365 Business Premium.

|Cybersecurity playbook  | Description  |
|---------|---------|
| :::image type="content" source="media/m365bp-cyber-security-playbook.png" alt-text="Screenshot of cybersecurity playbook for small business"::: | In this library: <ul><li>[Downloadable poster](https://download.microsoft.com/download/9/c/1/9c167271-8209-492e-acc2-38a39d1834c2/m365bp-cybersecurity-playbook.pdf) that guides you through the process of configuring Microsoft 365 Business Premium for Zero Trust.</li><li>Guidance for small and medium-sized businesses who aren’t security experts and need some help getting started.</li><li>Steps to secure unmanaged (bring your own device, or BYOD) and managed devices.</li><li>Recommendations and best practices for all employees, including tenant admins and security operations.</li></ul> |

See the following resources:

- [Microsoft 365 Business Premium - Productivity and cybersecurity for small business](/microsoft-365/business-premium/)
- [Microsoft 365 Business Premium resources for partners and small business](/microsoft-365/business/)

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly  | Multifactor authentication (MFA) is turned on by using security defaults (or with Conditional Access). This configuration requires users to register for MFA. It also disables access through legacy authentication (devices that don’t support modern authentication) and requires admins to authenticate every time they sign in.  |
| Use least privileged access | Guidance is provided for protecting administrative accounts and not using these accounts for user tasks. |
| Assume breach | Protection against malware and other cybersecurity threats is increased by using preset security policies. Guidance is provided for training your team to set up unmanaged (bring-your-own-device, or BYOD) devices, use email securely, and collaborate and share more securely. Additional guidance is provided to secure managed devices (devices that your organization owns).  |

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

Guidance is available to help customers review permissions and administrative access granted to partners. Guidance is also available to help Microsoft Managed Security Service Providers (MSSPs) integrate with their business customers’ tenants. See the following articles: 

- [Review partner administrative privileges](/microsoft-365/commerce/review-partner-admin-privileges) 
- [Configure managed security service provider integration](/microsoft-365/security/defender-endpoint/configure-mssp-support)

Resources are available to help you as a Microsoft partner to manage your customers’ security settings, and to help protect their devices and data. Microsoft 365 Lighthouse integrates with [Microsoft 365 Business Premium](/microsoft-365/business-premium/), [Microsoft Defender for Business](/microsoft-365/security/defender-business/mdb-overview), and [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/). 

The Defender for Endpoint APIs can be used to integrate device security capabilities in Microsoft 365 Business Premium with remote monitoring and management (RMM) tools and professional service automation (PSA) software. See the following articles:

- [Integrate Microsoft endpoint security with your RMM tools and PSA software](/microsoft-365/security/defender-business/mdb-partners#integrate-microsoft-endpoint-security-with-your-rmm-tools-and-psa-software)
- [Use Microsoft 365 Lighthouse to secure and manage your customers’ devices and data](/microsoft-365/security/defender-business/mdb-partners#use-microsoft-365-lighthouse-to-secure-and-manage-your-customers-devices-and-data)
- [Help for partners (general information and support)](https://support.microsoft.com/topic/help-for-partners-ae811622-b838-4f62-b7e9-659627374963)

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | Partner resources are available to help Microsoft partners configure and manage their customers’ identity and access methods and policies. |
|  Use least privileged access | Partners can configure integration with customer tenants. Customers can review permissions and administrative access granted to partners. |
| Assume breach | Microsoft 365 Lighthouse integrates with Microsoft threat protection capabilities for small and medium-sized businesses. |

## Protect other SaaS apps you or your customers use

You or your small business customers likely use other Software as a Service (SaaS) applications, such as Salesforce, Adobe Creative Cloud, and DocuSign. You can integrate these applications with Microsoft Entra ID and include these in your MFA and Conditional Access policies. 

The Microsoft Entra application gallery is a collection of software as a service (SaaS) applications that have been pre-integrated with Entra ID. All you need to do is find the application in the gallery and add it to your environment. Then, the application will be available for you to include in the scope of your MFA and Conditional Access rules. See [Overview of the Microsoft Entra application gallery](/entra/identity/enterprise-apps/overview-application-gallery).

After you add SaaS apps to your environment, these apps will automatically be protected with Microsoft Entra MFA and the other protections provided by security defaults. If you're using Conditional Access policies instead of security defaults, you need to add these apps to the scope of your Conditional Access and related policies. See [Turn on MFA in Microsoft 365 Business Premium](/microsoft-365/business-premium/m365bp-turn-on-mfa).

Microsoft Entra ID determines when a user will be prompted for MFA based on factors such as location, device, role, and task. This functionality protects all applications registered with Microsoft Entra ID, including SaaS applications. See [Require users to do MFA when necessary](/entra/fundamentals/security-defaults#require-users-to-do-multifactor-authentication-when-necessary).

| Zero Trust principle | Met by |
|---------|---------|
| Verify explicitly | All SaaS apps you add require MFA for access. |
| Use least privileged access | Users must meet authentication requirements to use apps that access company data. |
| Assume breach | Factors, such as location, device, role, and task are considered when users are authenticated. MFA is used when necessary. |

## Additional Zero Trust documentation

Use additional Zero Trust content based on a documentation set or your role in your organization.

### Documentation set

Follow this table for the best Zero Trust documentation sets for your needs.

| Documentation set | Helps you... | Roles |
| --- | --- | --- |
| [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes | Apply Zero Trust protections from the C-suite to the IT implementation. | Security architects, IT teams, and project managers |
| [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. | IT teams and security staff |
| [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. | Security architects and IT implementers |
| [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to your Microsoft 365 tenant. | IT teams and security staff |
| [Zero Trust for Copilot for Microsoft 365](copilots/zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. | IT teams and security staff |
| [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. | IT teams and security staff |
| [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. | Partner developers, IT teams, and security staff |
| [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. | Application developers |

### Your role

Follow this table for the best documentation sets for your role in your organization.

| Role | Documentation set | Helps you... |
| --- | --- | --- |
| Security architect <br><br> IT project manager <br><br> IT implementer | [Adoption framework](adopt/zero-trust-adoption-overview.md) for phase and step guidance for key business solutions and outcomes| Apply Zero Trust protections from the C-suite to the IT implementation. |
| Member of an IT or security team | [Concepts and deployment objectives](deploy/overview.md) for general deployment guidance for technology areas | Apply Zero Trust protections aligned with technology areas. |
| Security architect <br><br> IT implementer | [Zero Trust Rapid Modernization Plan (RaMP)](zero-trust-ramp-overview.md) for project management guidance and checklists for easy wins | Quickly implement key layers of Zero Trust protection. |
| Member of an IT or security team for Microsoft 365 | [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=%2fsecurity%2fzero-trust%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fzero-trust%2ftoc.json) for stepped and detailed design and deployment guidance for Microsoft 365 | Apply Zero Trust protections to your Microsoft 365 tenant. |
| Member of an IT or security team for Microsoft Copilots | [Zero Trust for Copilot for Microsoft 365](copilots/zero-trust-microsoft-365-copilot.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Copilot for Microsoft 365. |
| Member of an IT or security team for Azure services | [Zero Trust for Azure services](azure-infrastructure-overview.md) for stepped and detailed design and deployment guidance | Apply Zero Trust protections to Azure workloads and services. |
| Partner developer or member of an IT or security team | [Partner integration with Zero Trust](integrate/overview.md) for design guidance for technology areas and specializations | Apply Zero Trust protections to partner Microsoft cloud solutions. |
| Application developer | [Develop using Zero Trust principles](develop/overview.md) for application development design guidance and best practices | Apply Zero Trust protections to your application. |