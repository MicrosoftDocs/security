---
title: How do I apply Zero Trust principles to Microsoft Copilot?
description: How to apply Zero Trust principles to Microsoft Copilot. 
ms.date: 04/02/2024
ms.service: security
author: BrendaCarter
ms.author: bcarter
ms.topic: concept-article
ms.collection: 
  - M365copilot
  - magic-ai-copilot 
  - msftsolution-copilot
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
ms.custom: [copilot-learning-hub]
---

# Apply principles of Zero Trust to Microsoft Copilot

**Summary:** To apply Zero Trust principles to Microsoft Copilot, you need to:

1. Implement security protections for web-grounded prompts to the Internet.
2. Add security protections for Microsoft Edge browser summarization.
3. Complete recommended security protections for Copilot for Microsoft 365.
4. Maintain security protections when using Microsoft Copilot and Copilot for Microsoft 365 together.

## Introduction

Microsoft Copilot or Copilot is an AI companion in copilot.microsoft.com, Windows, Edge, Bing, and the Copilot mobile app. This article helps you implement security protections to keep your organization and data safe while using Copilot. By implementing these protections, you are building a foundation of Zero Trust.

Zero Trust security recommendations for Copilot focus on protection for user accounts, user devices, and the data that is in scope for the way you configure Copilot.

You can introduce Copilot in stages, from allowing Web-grounded prompts to the Internet to allowing both Web-grounded and Microsoft 365 Graph-grounded prompts to both the Internet and to your organization data. This article helps you understand the scope of each configuration and, consequently, the recommendations for preparing your environment with appropriate security protections.

## How does Zero Trust help with AI?

Security, especially data protection, is often a top concern when introducing AI tools into an organization. Zero Trust is a security strategy that verifies every user, device, and resource request to ensure that each of these is allowed. The term ‘zero trust’ refers to the strategy of treating each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to “never trust, always verify.”

As a leader in security, Microsoft provides a practical roadmap and clear guidance for implementing Zero Trust. Microsoft’s set of Copilots are built on top of existing platforms, which inherit the protections applied to those platforms. For the details of applying Zero Trust to Microsoft’s platforms, see the [Zero Trust Guidance Center](/security/zero-trust/). By implementing these protections, you are building a foundation of Zero Trust security.

This article draws from that guidance to prescribe the Zero Trust protections that relate to Copilot. 

## What’s included in this article

This article walks through the security recommendations that apply in four stages. This provides a path for you to introduce Copilot into your environment while you apply security protections for users, devices, and the data accessed by Copilot.


| Stage | Configuration | Components to secure |
| --- | --- | --- |
| 1 | Web-grounded prompts to the Internet | Basic security hygiene for users and devices using identity and access policies. |
| 2 | Web-grounded prompts to the Internet with Edge browser page summarization enabled | Your organization data on local, intranet, and cloud locations that Copilot in Edge can summarize. |
| 3 | Web-grounded prompts to the Internet and access to Copilot for Microsoft 365 | All components affected by Copilot for Microsoft 365. |
| 4 | Web-grounded prompts to the Internet and access to Copilot for Microsoft 365 with Edge browser page summarization enabled | All the components listed above. |

## Stage 1. Start with security recommendations for web-grounded prompts to the Internet

The simplest configuration of Copilot provides AI assistance with web-grounded prompts. 

:::image type="content" source="../media/copilot/microsoft-copilot-web-grounded-prompts.svg" alt-text="Diagram of Copilot for Microsoft and the processing of Web-grounded prompts." lightbox="../media/copilot/microsoft-copilot-web-grounded-prompts.svg":::

In the illustration:

- Users can interact with Copilot through copilot.microsoft.com, Windows, Bing, the Edge browser, and the Copilot mobile app.
- Prompts are Web-grounded. Copilot only uses publicly available data to respond to prompts.

With this configuration, your organization data isn’t included in the scope of data that Copilot references. 

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

From the Microsoft Edge sidebar, Microsoft Copilot helps you get answers and inspirations from across the web and, if enabled, from some types of information displayed in open browser tabs.

:::image type="content" source="../media/copilot/microsoft-copilot-edge-summarization-enabled.svg" alt-text="Diagram of Web-grounded prompts in Edge with browser tab summarization enabled." lightbox="../media/copilot/microsoft-copilot-edge-summarization-enabled.svg":::

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

This illustration shows the data sets available to Microsoft Copilot in Edge with browser summarization enabled.

:::image type="content" source="../media/copilot/microsoft-copilot-edge-data-sets.svg" alt-text="Diagram of the data sets available to Microsoft Copilot in Edge." lightbox="../media/copilot/microsoft-copilot-edge-data-sets.svg":::

### Recommendations for E3 and E5

- Implement Intune [app protection policies (APP)](/microsoft-365/security/office-365-security/zero-trust-identity-device-access-policies-common#app-protection-policies) for data protection. APP can prevent the inadvertent or intentional copying of Copilot-generated content to apps on a device that aren’t included in the list of permitted apps. APP can limit the blast radius of an attacker using a compromised device.

- Turn on [Microsoft Defender for Office 363 Plan 1](/microsoft-365/security/defender/eval-defender-office-365-overview), which include Exchange Online Protection (EOP) for Safe Attachments, Safe Links, advanced phishing thresholds and impersonation protection, and real-time detections.


## Stage 3. Complete security protections recommended for Copilot for Microsoft 365

Copilot for Microsoft 365 can use the following data sets to process Graph-grounded prompts:

- Your Microsoft 365 tenant data
- Internet data through Bing search (if [enabled](/microsoft-365-copilot/manage-public-web-access))
- The data used by Copilot-enabled plug-ins and connectors

:::image type="content" source="../media/copilot/microsoft-365-copilot-graph-grounded-prompts.svg" alt-text="Diagram of Copilot for Microsoft 365 and the processing of Graph-grounded prompts." lightbox="../media/copilot/microsoft-365-copilot-graph-grounded-prompts.svg":::

For more information, see [Apply principles of Zero Trust to Microsoft Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md).

### Recommendations for E3

Implement the following:

- [Intune device management and device compliance requirement policies](/security/zero-trust/zero-trust-microsoft-365-copilot#step-4-deploy-or-validate-your-device-management-and-protection)
- [Data protection in your Microsoft 365 tenant](/security/zero-trust/zero-trust-microsoft-365-copilot#step-1-deploy-or-validate-your-data-protection)

   - Sensitivity labels

   - Data Loss Prevention (DLP) policies

   - Retention policies

- [Turn on Microsoft Defender for Endpoint](/microsoft-365/security/defender/eval-defender-endpoint-overview)

### Recommendations for E5

Implement the recommendations for E3 and the following:

 - Use a greater range of classifiers to find sensitive info.
- Automate your retention labels.
- Try out the [Plan 2 capabilities in Defender for Office 365](/microsoft-365/security/office-365-security/mdo-about#what-is-the-difference-between-plan-1-and-plan-2-defender-for-office-365), which include post-breach investigation, hunting, and response, automation, and simulation.
- Turn on [Microsoft Defender for Cloud Apps](/microsoft-365/security/defender/eval-defender-mcas-overview).
- Configure Defender for Cloud Apps to [discover cloud apps and monitor and audit their behavior](/microsoft-365/security/defender/eval-defender-mcas-architecture#discovering-cloud-apps).

## Stage 4. Maintain security protections while you use Microsoft Copilot and Copilot for Microsoft 365 together

With a license for Copilot for Microsoft 365, you will see a **Work/Web** toggle control in the Edge browser, Windows, and Bing search that allows you to switch between using:

- Graph-grounded prompts that are sent to Copilot for Microsoft 365 (toggle set to **Work**).
- Web-grounded prompts that primarily use internet data (toggle set to **Web**).

Here’s an example for copilot.microsoft.com.

:::image type="content" source="../media/copilot/microsoft-copilot-example-copilot.microsoft-com.png" alt-text="Example screenshot of Microsoft Copilot for Microsoft Bing." lightbox="../media/copilot/microsoft-copilot-example-copilot.microsoft-com.png":::

This illustration shows the flow of Graph- and Web-grounded prompts.

:::image type="content" source="../media/copilot/logical-architecture-microsoft-copilot.svg" alt-text="Diagram of the logical architecture of Microsoft Copilot showing Graph and web-grounded prompts." lightbox="../media/copilot/logical-architecture-microsoft-copilot.svg":::

In the diagram:

- Users on devices with a license for Copilot for Microsoft 365 can choose **Work** or **Web** mode for Microsoft Copilot prompts.
- If **Work** is chosen, Graph-grounded prompts are sent to Copilot for Microsoft 365 for processing.
- If **Web** is chosen, Web-grounded prompts entered via Windows, Bing, or Edge use internet data in its processing.
- In the case of Edge and when enabled, Windows Copilot includes some types of data in open Edge tabs in its processing.

If the user does not have a license for Copilot for Microsoft 365, the **Work/Web** toggle is not displayed and all prompts are Web-grounded.

Here are the sets of accessible organization data for Microsoft Copilot, which include both Graph- and Web-grounded prompts.

:::image type="content" source="../media/copilot/microsoft-copilot-accessible-organization-data-sets.svg" alt-text="Diagram of the sets of accessible organization data for Microsoft Copilot for both Graph- and Web-grounded prompts." lightbox="../media/copilot/microsoft-copilot-accessible-organization-data-sets.svg":::
 
In the illustration, the yellow shaded blocks are for your organization data that is accessible through Copilot. Access to this data by a user through Copilot depends on the permissions to the data assigned to the user account. It can also depend on the status of the user’s device if conditional access  is configured for either the user or for access to the environment where the data resides. Following the principles of Zero Trust, this is data you want to protect in case an attacker compromises a user account or device. 

- For Graph-grounded prompts (toggle set to **Work**), this includes:

   - Your Microsoft 365 tenant data

   - Data for Copilot-enabled plug-ins and connectors

   - Internet data (if the web plug-in is enabled)

- For Web-grounded prompts from the Edge browser with open browser tab summarization enabled (toggle set to **Web**), this can include organization data that can be summarized by Copilot in Edge from local, intranet, and cloud locations.

Use this stage to verify your implementation of the following levels of security to prevent bad actors from using Copilot to access your sensitive data:

- [Deploy data security and compliance protections with Microsoft Purview](/purview/ai-microsoft-purview)
- [Configure minimum user permissions to data](zero-trust-microsoft-365-copilot.md#step-7-deploy-or-validate-minimum-user-permissions-to-data)
- [Deploy threat protection for cloud apps with Microsoft Defender for Cloud Apps](/defender-cloud-apps/what-is-defender-for-cloud-apps)

### Recommendations for E3

- Review your configuration and the features of [Defender for Office 365 Plan 1](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) and [Defender for Endpoint Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1) and implement additional capabilities as needed.
- Set up appropriate [levels of protection for Microsoft Teams](/security/zero-trust/zero-trust-microsoft-365-copilot#step-6-deploy-or-validate-secure-collaboration-for-microsoft-teams).

### Recommendations for E5

Implement the recommendations for E3 and extend the XDR capabilities in your Microsoft 365 tenant:

- Turn on [Microsoft Defender for Identity](/microsoft-365/security/defender/eval-defender-identity-overview).

- Review your configuration and implement additional capabilities as needed to increase your threat protection with the full Microsoft Defender XDR suite:

  - [Defender for Endpoint](/microsoft-365/security/defender/microsoft-365-security-center-mde)

  - [Defender for Office 365](/microsoft-365/security/defender/microsoft-365-security-center-mdo)

  - [Defender for Identity](/microsoft-365/security/defender/microsoft-365-security-center-mdi)

  - [Defender for Cloud Apps](/microsoft-365/security/defender/microsoft-365-security-center-defender-cloud-apps)

  - [Configure session policies](/defender-cloud-apps/session-policy-aad) for Defender for Cloud Apps

## Configuration summary

This figure summarizes Microsoft Copilot configurations and the resulting accessible data that Copilot uses to respond to prompts.

:::image type="content" source="../media/copilot/microsoft-copilot-configurations-resulting-accessible-data-table.svg" alt-text="A table showing Microsoft Copilot configurations and the resulting accessible data for Web- and Grapg-grounded prompts." lightbox="../media/copilot/microsoft-copilot-configurations-resulting-accessible-data-table.svg":::

This table includes Zero Trust recommendations for your chosen configuration. 

| Configuration | Accessible data | Zero Trust recommendations |
| --- | --- | --- |
| Without Copilot for Microsoft 365 licenses (**Work/Web** toggle not available) <br><br> AND <br><br> Edge browser page summarization **disabled** | For Web-grounded prompts, internet data only | None required, but highly recommended for overall security hygiene. |
| Without Copilot for Microsoft 365 licenses (**Work/Web** toggle not available) <br><br> AND <br><br> Edge browser page summarization **enabled** | For Web-grounded prompts: <br><br> - Internet data <br> - Organization data on local, intranet, and cloud locations that Copilot in Edge can summarize | For your Microsoft 365 tenant, see [Zero Trust for Copilot for Microsoft 365](/security/zero-trust/zero-trust-microsoft-365-copilot) and apply Zero Trust protections. <br><br> For organization data on local, intranet, and cloud locations, see [Manage devices with Intune Overview](/microsoft-365/solutions/manage-devices-with-intune-overview) for MAM and MDM policies. Also see [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection) for DLP policies. |
| With Copilot for Microsoft 365 licenses (**Work/Web** toggle available) <br><br> AND <br><br> Edge browser page summarization **disabled** | For Graph-grounded prompts: <br><br> - Microsoft 365 tenant data <br> - Internet data if the web plug-in is enabled <br>- Data for Copilot-enabled plug-ins and connectors <br><br> For Web-grounded prompts, only internet data	 | For your Microsoft 365 tenant, see [Zero Trust for Copilot for Microsoft 365](/security/zero-trust/zero-trust-microsoft-365-copilot) and apply Zero Trust protections. |
| With Copilot for Microsoft 365 licenses (**Work/Web** toggle available) <br><br> AND <br><br> Edge browser page summarization **enabled** | For Graph-grounded prompts: <br><br> - Microsoft 365 tenant data <br> - Internet data if the web plug-in enabled <br> - Data for Copilot-enabled plug-ins and connectors <br><br> For Web-grounded prompts: <br><br> - Internet data <br> - Organization data that can be rendered in an Edge browser page, including local, cloud, and intranet resources | For your Microsoft 365 tenant, see Zero Trust for Copilot for Microsoft 365 and apply Zero Trust protections. <br><br> For organization data on local, intranet, and cloud locations, see [Manage devices with Intune Overview](/microsoft-365/solutions/manage-devices-with-intune-overview) for MAM and MDM policies. Also see [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection) for DLP policies. |

## Next steps

See these additional articles for Zero Trust and Microsoft's Copilots:

- [Overview](apply-zero-trust-copilots-overview.md)
- [Microsoft Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md)
- [Microsoft Copilot for Security](zero-trust-microsoft-copilot-for-security.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- [Copilot in Edge](/copilot/edge)
- [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results)
- [Manage Copilot in Windows](/windows/client-management/manage-windows-copilot)
- [Manage access to public web content in Microsoft Copilot for Microsoft 365 responses](/microsoft-365-copilot/manage-public-web-access)
- [Data, Privacy, and Security for Microsoft Copilot for Microsoft 365](/microsoft-365-copilot/microsoft-365-copilot-privacy)
