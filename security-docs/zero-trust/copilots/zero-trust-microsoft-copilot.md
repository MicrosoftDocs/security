---
title: How do I apply Zero Trust principles to Microsoft 365 Copilot Chat for web-grounded prompts?
description: How to apply Zero Trust principles to Microsoft 365 Copilot Chat for web-grounded prompts. 
ms.date: 03/04/2025
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection:
- M365copilot
- msec-ai-copilot
- msftsolution-copilot
- msftsolution-scenario
- zerotrust-solution
- zerotrust-copilot
- trust-pod
ms.custom: [copilot-learning-hub]
---

# Apply principles of Zero Trust to Microsoft 365 Copilot Chat

**Summary:** To apply Zero Trust principles to Microsoft 365 Copilot Chat, you need to:

1. Implement security protections for web-grounded prompts to the Internet.
2. Add security protections for Microsoft Edge browser summarization.


## Introduction

Microsoft 365 Copilot Chat is an AI companion in the Microsoft 365 Copilot app, in Edge, and at the following URLs — M365copilot.com and Copilot.cloud.microsoft. It's provided for Entra account users with a [qualifying license](/copilot/manage#microsoft-365--chat-eligibility). Copilot Chat includes enterprise data protection. Enterprise data protection is not included in Copilot Chat for personal use (consumer version). This article helps you implement security protections to keep your organization and data safe while using Copilot Chat. By implementing these protections, you're building a foundation of Zero Trust.

Zero Trust security recommendations for Copilot Chat focus on protection for user accounts, user devices, and your organization data that can be summarized by Copilot Chat in Edge. 

## How does Zero Trust help with AI?

Security, especially data protection, is often a top concern when introducing AI tools into an organization. Zero Trust is a security strategy that verifies every user, device, and resource request to ensure that each of these is allowed. The term "zero trust" refers to the strategy of treating each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to “never trust, always verify.”

As a leader in security, Microsoft provides a practical roadmap and clear guidance for implementing Zero Trust. Microsoft’s set of Copilots are built on top of existing platforms, which inherit the protections applied to those platforms. For the details of applying Zero Trust to Microsoft’s platforms, see the [Zero Trust Guidance Center](/security/zero-trust/). By implementing these protections, you're building a foundation of Zero Trust security.

This article draws from that guidance to prescribe the Zero Trust protections that relate to Copilot. 

## What’s included in this article

This article walks through the security recommendations that apply in two stages. This provides a path for you to introduce Copilot Chat into your environment while you apply security protections for users, devices, and the data accessed by Copilot.


| Stage | Configuration | Components to secure |
| --- | --- | --- |
| 1 | Web-grounded prompts to the Internet | Basic security hygiene for users and devices using identity and access policies. |
| 2 | Web-grounded prompts to the Internet with Edge browser page summarization enabled | Your organization data on local, intranet, and cloud locations that Copilot in Edge can summarize. |


## Stage 1. Start with security recommendations for web-grounded prompts to the Internet

The simplest configuration of Copilot provides AI assistance with web-grounded prompts. 

:::image type="content" source="../media/copilot/microsoft-copilot-web-grounded-prompts.svg" alt-text="Diagram of Microsoft Copilot and the processing of Web-grounded prompts." lightbox="../media/copilot/microsoft-copilot-web-grounded-prompts.svg":::

In the illustration:

- Users can interact with Copilot Chat through M365copilot.com, Copilot.cloud.microsoft, the Microsoft 365 Copilot app, and Edge.
- Prompts are web-grounded. Copilot Chat only uses publicly available data to respond to prompts.
- Edge browser page summarization is not enabled.

With this configuration, your organization data isn’t included in the scope of data that Copilot Chat references. However, you need to ensure that browser page summarization is not enabled. As an admin, you can do this by using the [*EdgeEntraCopilotPageContext*](/copilot/manage#manage--chat-in-edge) group policy setting.



Use this stage to implement identity and access policies for users and devices to prevent bad actors from using Copilot. At a minimum, you must configure Conditional Access policies that require:

- [Multifactor authentication for all users](zero-trust-microsoft-365-copilot.md#step-2-deploy-or-validate-your-identity-and-access-policies)
- [Trusted and healthy devices](zero-trust-microsoft-365-copilot.md#step-4-deploy-or-validate-your-device-management-and-protection)

### Additional recommendations for Microsoft 365 E3

- For user account authentication and access, also configure the identity and access policies to [Block clients that don’t support modern authentication](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#block-clients-that-dont-support-multifactor-authentication).
- [Use Windows protection capabilities](zero-trust-microsoft-365-copilot.md#windows-protection-capabilities). 

### Additional recommendations for Microsoft 365 E5

Implement the recommendations for E3 and configure the following identity and access policies:

- [Require MFA when sign-in risk is medium or high](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#require-mfa-based-on-sign-in-risk)
- [High risk users must change their password](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#high-risk-users-must-change-password)


## Stage 2. Add security protections for Edge browser summarization

From the Microsoft Edge sidebar, Microsoft 365 Copilot Chat helps you get answers and inspirations from across the web and, if enabled, from some types of information displayed in open browser tabs. 

:::image type="content" source="../media/copilot/microsoft-copilot-edge-summarization-enabled.svg" alt-text="Diagram of Web-grounded prompts in Edge with browser tab summarization enabled." lightbox="../media/copilot/microsoft-copilot-edge-summarization-enabled.svg":::

If you disabled browser page summarization, you need to re-enable this feature. As an admin, you can do this by using the [*EdgeEntraCopilotPageContext*](/copilot/manage#manage--chat-in-edge) group policy setting.

Here are some examples of private or organization web pages and document types that Copilot in Edge can summarize:

- Intranet sites such as SharePoint, except embedded Office documents
- Outlook Web App
- PDFs, including those stored on the local device
- Sites not protected by Microsoft Purview DLP policies, Mobile Application Management (MAM) policies, or MDM policies

> [!NOTE]
> For the current list of document types supported by Copilot in Edge for analysis and summarization, see [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results).

Potentially sensitive organization sites and documents that Copilot in Edge can summarize could be stored in local, intranet, or cloud locations. This organization data can be exposed to an attacker who has access to the device and uses Copilot in Edge to quickly produce summarizations of documents and sites.

The organization data that can be summarized by Copilot in Edge can include:

- Local resources on the user’s computer

   PDFs or information displayed in an Edge browser tab by local apps that are not protected with MAM policies

- Intranet resources

   PDFs or sites for internal apps and services that are not protected by Microsoft Purview DLP policies, MAM policies, or MDM policies

- Microsoft 365 sites that are not protected by Microsoft Purview DLP policies, MAM policies, or MDM policies

- Microsoft Azure resources

   PDFs on virtual machines or sites for SaaS apps that are not protected by Microsoft Purview DLP policies, MAM policies, or MDM policies

- Third-party cloud product sites for cloud-based SaaS apps and services that are not protected by Microsoft Purview DLP policies, MAM policies, or MDA policies

Use this stage to implement levels of security to prevent bad actors from using Copilot to more quickly discover and access sensitive data. At a minimum, you must:

- [Deploy data security and compliance protections with Microsoft Purview](/purview/ai-microsoft-purview)
- [Configure minimum user permissions to data](zero-trust-microsoft-365-copilot.md#step-7-deploy-or-validate-minimum-user-permissions-to-data)
- [Deploy threat protection for cloud apps with Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps)

For more information about Copilot in Edge, see:

- [Copilot in Edge](/copilot/edge)
- [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results)

### Recommendations for E3 and E5

- Implement Intune [app protection policies (APP)](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#app-protection-policies) for data protection. APP can prevent the inadvertent or intentional copying of Copilot-generated content to apps on a device that aren’t included in the list of permitted apps. APP can limit the blast radius of an attacker using a compromised device.

- Turn on [Microsoft Defender for Office 363 Plan 1](/microsoft-365/security/defender/eval-defender-office-365-overview), which include Exchange Online Protection (EOP) for Safe Attachments, Safe Links, advanced phishing thresholds and impersonation protection, and real-time detections.



## Next steps

See these additional articles for Zero Trust and Microsoft's Copilots:

- [Overview](apply-zero-trust-copilots-overview.md)
- [Microsoft Microsoft 365 Copilot](zero-trust-microsoft-365-copilot.md)
- [Microsoft Copilot for Security](zero-trust-microsoft-copilot-for-security.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Copilot in Edge](/copilot/edge)
- [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results)
- [Manage access to public web content in Microsoft Microsoft 365 Copilot responses](/microsoft-365-copilot/manage-public-web-access)
- [Data, Privacy, and Security for Microsoft Microsoft 365 Copilot](/microsoft-365-copilot/microsoft-365-copilot-privacy)
