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

This solution builds on the Microsoft Information Protection solution guidance and guides you on how to use Defender for Cloud Apps to extend information protection to data in SaaS apps. You may want to review the guidance to gain better understanding of the overall workflow. For more information, see [Deploy an information protection solution with Microsoft Purview](/microsoft-365/compliance/information-protection-solution).

The key concepts surrounding information protection involves knowing your data, protecting your data, and preventing data loss. 

:::image type="content" source="media/saas-know-protect-prevent.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365 by knowing, protecting, and preventing data loss" lightbox="media/saas-know-protect-prevent.png":::


To protect data in SaaS apps, you must first identify and classify data. To identify your data, you need to define what is considered to be sensitive information for your organization. You can define sensitive information using the Microsoft Purview Information Protection portal and create sensitive information types and labels. Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services after they are created.


After identifying and classifying your data, you can then proceed to protect your data by applying sensitivity labels out to SaaS apps. 


To prevent data loss, you can create and apply data loss prevention (DLP) policies protection actions that such as encryption, access restrictions, and other actions. 


Use the following steps to guide you in using Microsoft 365 products so that you can apply information protection capabilities on SaaS apps:


|Step  |Description  |
|---------|---------|
|1     |  Discover sensitive information in SaaS apps       |
|2     |  Apply sensitivity labels to SaaS apps   |
|3     |  Extend DLP policies to cloud apps |
|4     | Protect your data  |
|5     | Monitor and report on your data |



## Discover sensitive information in SaaS apps

To discover sensitive information contained in SaaS apps, you'll need to:

1.	Enable the Microsoft Purvue Information Protection integration 
2.	Create policies to identify sensitive information in files 


By integrating Microsoft Purview Information Protection into Defender for Cloud Apps, you can use the full power of both services and secure files in your cloud, including:

- The ability to apply sensitivity labels as a governance action to files that match specific policies
- The ability to view all classified files in a central location
- The ability to investigate according to classification level, and quantify exposure of sensitive data over your cloud applications
- The ability to create policies to make sure classified files are being handled properly


For more information, see [How to integrate Microsoft Purview Information Protection with Defender for Cloud Apps](/defender-cloud-apps/azip-integration#how-to-integrate-microsoft-purview-information-protection-with-defender-for-cloud-apps).


Once you know the kinds of information you want to protect, it's time to create policies to detect them. 

You can create policies for **files** and for **sessions**. File policies scan the content of files stored in your API connected cloud apps. Session policies scan and protect files in real time on access to prevent data exfiltration, protect files on download, prevent the upload of unlabeled files.


Files are scanned using one of our supported inspection methods such as Data Classification Services. You can use Data Classification Services which uses classification decisions you've made across Office 365, Microsoft Purview Information Protection, and Defender for Cloud Apps to provide a unified labeling experience. This is the preferred content inspection method as it provides a consistent and unified experience across Microsoft products.


For more information, see [Microsoft Data Classification Services integration](/defender-cloud-apps/dcs-inspection).


## Apply sensitivity labels to SaaS apps
After discovering and classifying sensitive information, you need to apply sensitivity labels on them so that appropriate action can be taken to protect files. For example, a file that is labeled "Confidential" may be encrypted and have a "Confidential" watermark applied to it.


Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services. So when you want to define sensitive information, head over to the Microsoft Purview Information Protection portal to create them, and once defined they will be available in Defender for Cloud Apps.

For more information, see [Apply Microsoft Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).


## Extend DLP policies to SaaS apps

To help protect sensitive data from being exposed, use Microsoft Purview Data Loss Prevention (DLP) to monitor the actions that are being taken on items you've determined to be sensitive and to help prevent the unintentional sharing of those items. 

Depending on the SaaS apps that you have in your environment, you have various options to choose from to deploy a DLP solution. Use the following table to guide you in your decision making process:



Scenario | Tool 
:---|:---
Your environment has the following products:<br> <br> - Exchange Online email <br> - SharePoint Online sites <br>- OneDrive accounts <br>- Teams chat and channel messages <br>  - Microsoft Defender for Cloud Apps<br>  - Windows 10, Windows 11, and macOS (Catalina 10.15 and higher) devices <br> - On-premises repositories<br>- PowerBI sites | Use Microsoft Purview.  <br><br> <br><br> For more information, see [Learn about DLP](/microsoft-365/compliance/dlp-learn-about-dlp). |
Your organization uses other apps that are not covered in Microsoft Purview, but can be connected to Microsoft Defender for Cloud Apps such as: - Atlassian <br> - Azure  <br> - AWS <br> - Box  <br> - DocuSign <br>-Egnyte  <br> - GitHub  <br> - Google Workspace  <br> - GCP  <br> - NetDocuments  <br> - Office 365  <br> - Okta  <br> - OneLogin  <br> - Salesfoce  <br> - ServiceNow  <br> - Slack  <br> - Smartsheet  <br> - Webex  <br> - Workday  <br> - Zendesk| Use Microsoft Defender for Cloud Apps. <br><br> To use a DLP policy thats scoped to a specific non-Microsoft cloud app, the app must be connected to Defender for Cloud Apps. 





For more information, see [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps).
The apps that your organization uses are not yet supported in Microsoft Purvue but can be added using app connectors. |  Use Microsoft Defender for Cloud Apps.   <br><br> For more information, see [Connect apps](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).



 




## Protect your data


You can also apply sensitivity labels from Microsoft Purview Information Protection. For more information, see [Apply Microsoft Purview Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).



## Monitor your data