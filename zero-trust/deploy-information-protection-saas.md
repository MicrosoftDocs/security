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



## Discover sensitive information in SaaS apps

To discover sensitive information contained in SaaS apps, you'll need to:

1.	Enable the Microsoft Purvue Information Protection integration 
2.	Create policies to identify sensitive information in files 


By integrating Microsoft Purview Information Protection into Defender for Cloud Apps, you can use the full power of both services and secure files in your cloud, including:

- The ability to apply sensitivity labels as a governance action to files that match specific policies
- The ability to view all classified files in a central location
- The ability to investigate according to classification level, and quantify exposure of sensitive data over your cloud applications
- The ability to create policies to make sure classified files are being handled properly




## Apply sensitivity labels to SaaS apps
After discovering and classifying sensitive information, you need to apply sensitivity labels on them so that appropriate action can be applied to protect files. For example, a file that is labeled "Confidential" may be encrypted and have a "Confidential" watermark applied to it.


Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services. So when you want to define sensitive information, head over to the Microsoft Purview Information Protection portal to create them, and once defined they will be available in Defender for Cloud Apps.

For more information, see [Apply Microsoft Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).


## Extend DLP policies to SaaS apps
In Microsoft Purview, you implement data loss prevention by defining and applying DLP policies. With a DLP policy, you can identify, monitor, and automatically protect sensitive items across:

- Microsoft 365 services such as Teams, Exchange, SharePoint, and OneDrive
- Office applications such as Word, Excel, and PowerPoint
- Windows 10, Windows 11 and macOS (Catalina 10.15 and higher) endpoints
- non-Microsoft cloud apps
- on-premises file shares and on-premises SharePoint.




With data loss prevention (DLP) policies, you can identify, monitor, and automatically protect sensitive information.





Data loss prevention policies can use sensitivity labels and sensitive information types to identify sensitive information.


To protect information on sensitive information beyond the listed items, use Microsoft Defender for Cloud Apps....to....





You can scope DLP policies to Microsoft Defender for Cloud Apps to monitor, detect and take actions when sensitive items are used and shared via non-Microsoft cloud apps.

For more information, see [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps).

 

You can also apply sensitivity labels from Microsoft Purview Information Protection. For more information, see [Apply Microsoft Purview Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).