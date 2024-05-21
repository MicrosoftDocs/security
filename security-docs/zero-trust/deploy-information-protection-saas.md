---
title: Deploy information protection for SaaS apps
description: Learn how to deploy information protection for SaaS apps to prevent inadvertent exposure of sensitive information.
ms.date: 04/18/2024
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
ms.collection:
  -	m365solution-saas
  -	m365solution-scenario
  -	m365solution-zero-trust
  -	zerotrust-solution
  - highpri
---

# Step 3: Deploy information protection for SaaS apps 
 

While protecting access to apps and session activities are important, the data that SaaS apps contain may be one of the most critical resources to protect. Deploying information protection for SaaS apps is a key step in preventing inadvertent or malicious exposure of sensitive information.

[Microsoft Purview Information Protection](/purview/information-protection) is natively integrated in Microsoft 365 apps and services such as SharePoint, OneDrive, Teams, and Exchange. For other SaaS apps, you might want to integrate them with Microsoft Purview to ensure your sensitive data is protected wherever it is. There are various ways to integrate information protection with other apps you use. You can use Microsoft Defender for Cloud Apps to integrate labeling with apps or have an app developer integrate directly using an SDK. For more information, see [About Microsoft Information Protection SDK](/information-protection/develop/overview). 
  
This step builds on the [Deploy information protection with Microsoft Purview](/microsoft-365/compliance/information-protection-solution) solution guidance and guides you on how to use Defender for Cloud Apps to extend information protection to data in SaaS apps. You may want to review the guidance to gain a better understanding of the overall workflow.

The scope of this article focuses on protecting Microsoft Office and PDF files and document repositories within SaaS applications. 

The key concepts surrounding information protection involves knowing your data, protecting your data, and preventing data loss. The following diagram shows how to perform these key functions with the Purview compliance portal and the Defender for Cloud Apps portal.

:::image type="content" source="./media/information-protection-saas-apps.svg" alt-text="Diagram of the process of knowing your data, protecting your data, and preventing data loss with the Purview compliance portal and the Defender for Cloud Apps portal." lightbox="media/information-protection-saas-apps.svg":::

In this diagram:

- To protect data in SaaS apps, you must first determine the information in your organization that is sensitive. After doing that, check to see if any of the sensitive information types (SITs) map to the determined sensitive information. If none of the SITs meet your needs, you can modify them or create custom SITs with the Microsoft Purview compliance portal.
- Using the defined SITs, you can discover items that contain sensitive data in SaaS apps.

    >[!TIP]
    >To learn about the full list of supported apps for Microsoft Purview Information Protection, see [Information Protection](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps#information-protection)

- After discovering items that contain sensitive data, you can extend labels to SaaS apps and then apply them.
- To prevent data loss, you can define and then extend data loss prevention (DLP) policies. With a DLP policy, you can identify, monitor, and automatically protect sensitive items across services. An example of a protective action of DLP policies is showing a pop-up policy tip to a user when they try to share a sensitive item inappropriately. Another example is blocking the sharing of sensitive items.

Use the following steps to apply information protection capabilities for your SaaS apps.

## Discover sensitive information in SaaS apps

To discover sensitive information contained in SaaS apps, you'll need to:

- Enable the Microsoft Purview Information Protection integration with Defender for Cloud Apps.
- Create policies to identify sensitive information in files.

Microsoft Purview Information Protection is a framework that includes Defender for Cloud Apps. Integrating Defender for Cloud Apps in Microsoft Purview will help you better protect sensitive information in your organization. For more information, see [How to integrate Microsoft Purview Information Protection with Defender for Cloud Apps](/defender-cloud-apps/azip-integration#how-to-integrate-microsoft-purview-information-protection-with-defender-for-cloud-apps).

Once you know the kinds of information you want to protect, you create policies to detect them. You can create policies for:

- **Files:** File policies scan the content of files stored in your connected cloud apps via API, for supported apps.
- **Sessions:** Session policies scan and protect files in real time upon access to prevent data exfiltration, protect files on download, and prevent the upload of unlabeled files.

For more information, see [Microsoft Data Classification Services integration](/defender-cloud-apps/dcs-inspection).

## Apply sensitivity labels to protect data

After discovering and sorting sensitive information, you can apply sensitivity labels. When a sensitivity label is applied to a document, any configured protection settings for that label are enforced on the content. For example, a file that is labeled "Confidential" may be encrypted and have its access limited. Access limitations can include individual user accounts or groups.

Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitivity types and labels are available throughout both services. When you want to define sensitive information, use the Microsoft Purview compliance portal to create them and they will be available in Defender for Cloud Apps.

Defender for Cloud Apps lets you automatically apply sensitivity labels from Microsoft Purview Information Protection. These labels are applied to files as a file policy governance action and, depending on the label configuration, can apply encryption for another layer of protection.

For more information, see [Apply Microsoft Purview Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).

## Extend DLP policies to SaaS apps

Depending on the SaaS apps that you have in your environment, you have various options to choose from to deploy a DLP solution. Use the following table to guide you in your decision-making process.

| Scenario | Tool |
|:---|:---|
| Your environment has the following products:<br> <br> - Exchange Online email <br> - SharePoint Online sites <br>- OneDrive accounts <br>- Teams chat and channel messages <br>  - Microsoft Defender for Cloud Apps<br>  - Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices <br> - On-premises repositories<br>- Power BI sites | Use Microsoft Purview.  <br><br> For more information, see [Learn about DLP](/microsoft-365/compliance/dlp-learn-about-dlp). | 
| Your organization uses other apps that aren't covered in Microsoft Purview, but can be connected to Microsoft Defender for Cloud Apps via API such as:<br><br> - Atlassian <br> - Azure  <br> - AWS <br> - Box  <br> - DocuSign <br>- Egnyte  <br> - GitHub  <br> - Google Workspace  <br> - GCP  <br> - NetDocuments  <br> - Office 365  <br> - Okta  <br> - OneLogin  <br> - Salesforce  <br> - ServiceNow  <br> - Slack  <br> - Smartsheet  <br> - Webex  <br> - Workday  <br> - Zendesk| Use Defender for Cloud Apps. <br><br> To use a DLP policy that's scoped to a specific non-Microsoft cloud app, the app must be connected to Defender for Cloud Apps. For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps). |
| The apps that your organization uses aren't yet supported in Defender for Cloud Apps via API, but can be added using app connectors and you can use session policies to apply DLP policies in real time. | Use Defender for Cloud Apps. <br><br> For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps) and [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps). |

For guidance on licensing, see [Microsoft 365 guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## Monitor your data

Now that your policies are in place, you'll want to check the Microsoft Defender portal to monitor the effect of your policies and remediate incidents. Microsoft Defender XDR gives you visibility into DLP alerts and incidents from Microsoft Purview and Defender for Cloud apps in a single pane of glass.

Your security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats.

For more information, see [Microsoft Defender portal](/microsoft-365/security/defender/microsoft-365-defender-portal).
