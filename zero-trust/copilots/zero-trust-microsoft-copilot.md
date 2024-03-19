---
title: Apply principles of Zero Trust to Microsoft Copilot
description: Learn how to secure Microsoft Copilot with Zero Trust principles. 
ms.date: 01/26/2024
ms.service: security
author: bcarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - M365copilot 
  - msftsolution-copilot
  - msftsolution-scenario
  - zerotrust-solution
  - zerotrust-azure
---

# Apply principles of Zero Trust to Microsoft Copilot

**Summary:** To apply Zero Trust principles to Microsoft Copilot, you need to determine your desired configuration of Microsoft Copilot to identify the data sets that can be analyzed and summarized, and then apply Zero Trust principles to those data sets and their access.

## Introduction

Before you introduce Microsoft Copilot into your environment, Microsoft recommends that you build a strong foundation of security. Fortunately, guidance for a strong security foundation exists in the form of [Zero Trust](../zero-trust-overview.md). The Zero Trust security strategy treats each connection and resource request as though it originated from an uncontrolled network and a bad actor. Regardless of where the request originates or what resource it accesses, Zero Trust teaches us to "never trust, always verify."

Microsoft Copilot is an AI companion that works everywhere you do and intelligently adapts to your needs. You can ask Microsoft Copilot questions, known as prompts, and it will return results. You can access Microsoft Copilot in Windows, Edge, Bing, Microsoft 365, and the Copilot mobile app.

For Copilot in Windows, Edge, Bing, and the [Copilot mobile app](https://www.microsoft.com/copilot-app), responses to your prompts use internet data and can:

- Chat using text, voice, and images.
- Summarize documents and web pages.
- Use plugins and Copilot GPTs.

With a license for Copilot for Microsoft 365, you will see a **Work/Web** toggle control in the Edge browser, Windows, and Bing search that allows you to switch between using:

- Graph-grounded prompts that are sent to Copilot for Microsoft 365 (toggle set to **Work**).
- Web-grounded prompts that primarily use internet data (toggle set to **Web**).

Here’s an example for Microsoft Bing.

>> Add

The exception is Copilot in Edge, which can summarize some types of data in open browser tabs if enabled.

## Logical architecture

Here is the logical architecture for Microsoft Copilot.

>> Add

<!---

:::image type="content" source="../media/copilot/logical-architecture-microsoft-copilot.svg" alt-text="Diagram of the logical architecture for Microsoft Copilot." lightbox="../media/copilot/logical-architecture-microsoft-copilot.svg":::

--->

 
In the diagram:

- Users on devices with a license for Copilot for Microsoft 365 can choose *Work* or **Web** mode for Microsoft Copilot prompts.
- If **Work** is chosen, Graph-grounded prompts are sent to Copilot for Microsoft 365 for processing.
- If **Web** is chosen, Web-grounded prompts entered via Windows, Bing, or Edge use internet data in its processing.
- In the case of Edge and when enabled, Windows Copilot includes some types of data in open Edge tabs in its processing.

If the user does not have a license for Copilot for Microsoft 365, the **Work/Web** toggle is not displayed and all prompts are Web-grounded.

## Copilot for Microsoft 365

Copilot for Microsoft 365 can use the following data sets to process Graph-grounded prompts:

- Your Microsoft 365 tenant data
- Internet data through Bing search (if [enabled](/microsoft-365-copilot/manage-public-web-access))
- The data used by Copilot-enabled plug-ins and connectors

>> Add

## Copilot in Edge

From the Microsoft Edge sidebar, Microsoft Copilot helps you get answers and inspirations from across the web and, if enabled, from some types of information displayed in open browser tabs. Here are some examples of private or organization web pages and document types that Copilot in Edge can summarize:

- Intranet sites such as SharePoint, except embedded Office documents
- Outlook Web App
- PDFs, including those stored on the local device
- Sites not protected by Microsoft Purview DLP policies, Mobile Application Management (MAM) policies, or MDM policies


> [!NOTE]
> For the current list of document types supported by Copilot in Edge for analysis and summarization, see [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results).

This illustration summarizes the sets of data that are available to Microsoft Copilot in Edge.

>> Add 

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


For more information about Copilot in Edge, see:

- [Copilot in Edge](/copilot/edge)
- [Copilot in Edge webpage summarization behavior](/DeployEdge/edge-learnmore-copilot-page-summary-results)


## Microsoft Copilot configurations and accessible organization data

Here are the sets of accessible organization data for Microsoft Copilot, which include both Graph- and Web-grounded prompts.

>> Add
 
In the illustration, the yellow shaded blocks are for your organization data that is accessible through Copilot. Access to this data by a user through Copilot depends on the permissions to the data assigned to the user account. It can also depend on the status of the user’s device if conditional access  is configured for either the user or for access to the environment where the data resides. Following the principles of Zero Trust, this is data you want to protect in case an attacker compromises a user account or device. 

- For Graph-grounded prompts (toggle set to **Work**), this includes:

   - Your Microsoft 365 tenant data

   - Data for Copilot-enabled plug-ins and connectors

   - Internet data (if the web plug-in is enabled)

- For Web-grounded prompts from the Edge browser with open browser tab summarization enabled (toggle set to **Web**), this can include organization data that can be summarized by Copilot in Edge from local, intranet, and cloud locations.

This figure summarizes Microsoft Copilot configurations and the resulting accessible data that Copilot uses to respond to prompts.

>>Add table figure

This table includes Zero Trust recommendations for your chosen configuration. 

| Configuration | Accessible data | Zero Trust recommendations |
| --- | --- | --- |
| Without Copilot for Microsoft 365 licenses (**Work/Web** toggle not available) <br><br> AND <br><br> Edge browser page summarization **disabled** | For Web-grounded prompts, internet data only | None required, but highly recommended for overall security hygiene. |
| Without Copilot for Microsoft 365 licenses (**Work/Web** toggle not available) <br><br> AND <br><br> Edge browser page summarization **enabled** | For Web-grounded prompts: <br><br> - Internet data <br> - Organization data on local, intranet, and cloud locations that Copilot in Edge can summarize | For your Microsoft 365 tenant, see [Zero Trust for Copilot for Microsoft 365](/security/zero-trust/zero-trust-microsoft-365-copilot) and apply Zero Trust protections. <br><br> For organization data on local, intranet, and cloud locations, see [Manage devices with Intune Overview](/microsoft-365/solutions/manage-devices-with-intune-overview) for MAM and MDM policies. Also see [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection) for DLP policies. |
| With Copilot for Microsoft 365 licenses (**Work/Web** toggle available) <br><br> AND <br><br> Edge browser page summarization **disabled** | For Graph-grounded prompts: <br><br> - Microsoft 365 tenant data <br> - Internet data if the web plug-in is enabled <br>- Data for Copilot-enabled plug-ins and connectors <br><br> For Web-grounded prompts, only internet data	 | For your Microsoft 365 tenant, see [Zero Trust for Copilot for Microsoft 365](/security/zero-trust/zero-trust-microsoft-365-copilot) and apply Zero Trust protections. |
| With Copilot for Microsoft 365 licenses (**Work/Web** toggle available) <br><br> AND <br><br> Edge browser page summarization **enabled** | For Graph-grounded prompts: <br><br> - Microsoft 365 tenant data <br> - Internet data if the web plug-in enabled <br> - Data for Copilot-enabled plug-ins and connectors <br><br> For Web-grounded prompts: <br><br> - Internet data <br> - Organization data that can be rendered in an Edge browser page, including local, cloud, and intranet resources | For your Microsoft 365 tenant, see Zero Trust for Copilot for Microsoft 365 and apply Zero Trust protections. <br><br> For organization data on local, intranet, and cloud locations, see [Manage devices with Intune Overview](/microsoft-365/solutions/manage-devices-with-intune-overview) for MAM and MDM policies. Also see [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection) for DLP policies. |

## Next steps

Also see:

- [Overview of applying Zero Trust to Copilots from Microsoft](apply-zero-trust-copilots-overview.md)
- [Apply principles of Zero Trust to Microsoft Copilot for Microsoft 365](zero-trust-microsoft-365-copilot.md)

## References

Refer to these links to learn about the various services and technologies mentioned in this article.

- Copilot in Edge
- Copilot in Edge webpage summarization behavior
- Copilot in Windows 
- Manage access to public web content in Microsoft Copilot for Microsoft 365 responses
- Data, Privacy, and Security for Microsoft Copilot for Microsoft 365
