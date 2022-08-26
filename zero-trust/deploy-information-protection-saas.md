---
title: Deploy information protection for SaaS apps
description: 
ms.date: 04/15/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Step 3: Deploy information protection for SaaS apps 
 

While protecting access to apps and session activities are important, the data that SaaS apps contain may be one of the most critical resources that must be protected. Deploying information protection for SaaS apps is a key step in preventing inadvertent exposure of sensitive information.

Microsoft Purview Information Protection is natively integrated in Microsoft 365 apps and services such as SharePoint, OneDrive, Teams and Exchange, but for other SaaS apps you might want to implement integration to ensure your sensitive data is protected wherever it is. There are various ways you to integrate information protection with other apps you use. You can use Defender for Cloud Apps to integrate labeling with apps or have an app developer integrate directly using a SDK. For more information see, [About Microsoft Information Protection SDK](/information-protection/develop/overview). 
  

This solution builds on the Microsoft Purview Information Protection solution guidance and is scoped to guide you on how to use Defender for Cloud Apps to extend information protection to data in SaaS apps. You may want to review the guidance to gain better understanding of the overall workflow. For more information, see [Deploy an information protection solution with Microsoft Purview](/microsoft-365/compliance/information-protection-solution). 

The scope of this article focuses on protecting Office and PDF files and document repositories within SaaS applications. 

>[!TIP]
> While the scope of this article is focused on protecting files within SaaS applications, there are also developer related information available. For more information about developer related content such as building applications that use Microsoft Information Protection (MIP) SDK, see [About Microsoft Information Protection SDK](/information-protection/develop/overview).


The key concepts surrounding information protection involves knowing your data, protecting your data, and preventing data loss.



:::image type="content" source="media/saas-know-protect-prevent.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365 by knowing, protecting, and preventing data loss" lightbox="media/saas-know-protect-prevent.png":::

In this illustration:

- To protect data in SaaS apps, you must first determine what information in your organization has that's considered to be sensitive information. After doing that, check to see if any of the sensitive information types (SIT) map to the type of information. If none of the information types meet your needs, you can modify them or create your custom SIT. You can define sensitive information types using the Microsoft Purview compliance portal.
- Using the defined sensitive information types, you can discover items that contain sensitive data in SaaS apps.

    >[!TIP]
    >To learn about the full list of supported apps for Microsoft Purview Information Protection, see [Information Protection](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps#information-protection)

- After discovering items that contain sensitive data, you can extend labels out to SaaS apps and then apply them.
- To prevent data loss, you can define then extend data loss prevention (DLP) policies. With a DLP policy, you can identify, monitor, and automatically protect sensitive items across services. Some examples of the protective actions of DLP policies include showing a pop-up policy tip to a user when a user tries to share a sensitive item inappropriately. Other examples include block the sharing of data, and  sensitive items being locked and moved to a secure quarantine location.


Use the following steps to guide you in using Microsoft 365 products so that you can apply information protection capabilities on SaaS apps:


|Step  |Description  
|---------|---------|---------|
|1     |  Discover sensitive information in SaaS apps       
|2     |  Apply sensitivity labels to protect data  
|3    |  Extend DLP policies to cloud apps 
|4    |  Monitor and report on your data 





## Discover sensitive information in SaaS apps

To discover sensitive information contained in SaaS apps, you'll need to:

1.	Enable the Microsoft Purview Information Protection integration 
2.	Create policies to identify sensitive information in files 


Microsoft Purview Information Protection is a framework that includes Defender for Cloud Apps. Integrating Defender for Cloud Apps in Microsoft Purview will help you better protect sensitive information in your organization. 


For more information, see [How to integrate Microsoft Purview Information Protection with Defender for Cloud Apps](/defender-cloud-apps/azip-integration#how-to-integrate-microsoft-purview-information-protection-with-defender-for-cloud-apps).


Once you know the kinds of information you want to protect, it's time to create policies to detect them. 

You can create policies for:
- Files
- Sessions


File policies scan the content of files stored in your connected cloud apps via API, for supported apps. 

Session policies scan and protect files in real time on access to prevent data exfiltration, protect files on download, prevent the upload of unlabeled files.


For more information, see [Microsoft Data Classification Services integration](/defender-cloud-apps/dcs-inspection).


## Apply sensitivity labels to protect data
After discovering and sorting sensitive information, you can apply sensitivity labels. When a sensitivity label is applied to a document, any configured protection settings for that label are enforced on the content. For example, a file that is labeled "Confidential" may be encrypted, and access may be limited such as,  to a specific group of people, or just employees.

Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services. So when you want to define sensitive information, head over to the Microsoft Purview compliance portal to create them, and once defined they will be available in Defender for Cloud Apps.


Defender for Cloud Apps lets you automatically apply sensitivity labels from Microsoft Purview Information Protection. These labels will be applied to files as a file policy governance action, and depending on the label configuration, can apply encryption for additional protection.

For more information, see [Apply Microsoft Purview Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).


## Extend DLP policies to SaaS apps

Depending on the SaaS apps that you have in your environment, you have various options to choose from to deploy a DLP solution. Use the following table to guide you in your decision making process:


Scenario | Tool 
:---|:---
Your environment has the following products:<br> <br> - Exchange Online email <br> - SharePoint Online sites <br>- OneDrive accounts <br>- Teams chat and channel messages <br>  - Microsoft Defender for Cloud Apps<br>  - Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices <br> - On-premises repositories<br>- PowerBI sites | Use Microsoft Purview.  <br><br> <br><br> For more information, see [Learn about DLP](/microsoft-365/compliance/dlp-learn-about-dlp). |
Your organization uses other apps that are not covered in Microsoft Purview, but can be connected to Microsoft Defender for Cloud Apps via API such as:<br><br> - Atlassian <br> - Azure  <br> - AWS <br> - Box  <br> - DocuSign <br>- Egnyte  <br> - GitHub  <br> - Google Workspace  <br> - GCP  <br> - NetDocuments  <br> - Office 365  <br> - Okta  <br> - OneLogin  <br> - Salesfoce  <br> - ServiceNow  <br> - Slack  <br> - Smartsheet  <br> - Webex  <br> - Workday  <br> - Zendesk| Use Microsoft Defender for Cloud Apps. <br><br> To use a DLP policy thats scoped to a specific non-Microsoft cloud app, the app must be connected to Defender for Cloud Apps. For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).
The apps that your organization uses are not yet supported in Microsoft Defender for Cloud via API, but can be added using app connectors, and you can use session policies to apply DLP policies in real time. | Use Microsoft Defender for Cloud Apps. <br><br> For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps) and [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps).

 
For guidance on licensing, see [Microsoft 365 guidance for security & compliance](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).




## Monitor your data

Now that your policies are in place, you'll want to check the Microsoft 365 Defender portal to monitor the impact of the policies you've put into place and remediate incidents. Microsoft 365 Defender gives you visibility into DLP alerts and incidents from Microsoft Purview as well as Defender for Cloud apps in a single pane of glass.


 Security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats.


For more information, see [Microsoft 365 Defender portal](/microsoft-365/security/defender/microsoft-365-defender-portal).



