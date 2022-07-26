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
 

While protecting access to apps and session activities are important, the data that SaaS apps access may be one of the most critical resources that must be protected. Deploying information protection for SaaS apps is a key step in preventing inadvertent exposure of sensitive information.

This solution builds on the Microsoft Information Protection solution guidance and guides you on how to use Defender for Cloud Apps to extend information protection to data in SaaS apps.



:::image type="content" source="media/saas-information-protection-flow.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365" lightbox="media/saas-information-protection-flow.png":::


:::image type="content" source="media/information-protection-saas-flow.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365" lightbox="media/information-protection-saas-flow.png":::


To protect data in SaaS apps, you must first identify and classify data. To identify your data, you need to define what is considered to be sensitive information for your organization. You can define sensitive information using the Microsoft Purview Information Protection portal and create sensitive information types and labels. Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services after they are created.


After identifying and classifying your data, you can then proceed to protect your data by applying sensitivity labels out to SaaS apps. 


To prevent data loss, you can create and apply data loss prevention (DLP) policies protection actions that such as encryption, access restrictions, and other actions. 


Use the following steps to guide you in using Microsoft 365 products so that you can apply information protection capabilities on SaaS apps:


|Step  |Description  |
|---------|---------|
|1     |  Discover and classify sensitive data in SaaS apps       |
|2     |  Apply sensitivity labels to SaaS apps   |
|3     |  Extend DLP policies to cloud apps |



## Discover and classify sensitive information in SaaS apps

The first step in discovering which data is being used in your organization, is to connect cloud apps used in your organization to Defender for Cloud Apps. Once connected, Defender for Cloud Apps can scan data, add classifications, and enforce policies and controls. 

You can use one of the following steps to connect apps:
- [Use an app connector](/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
- [Use Conditional Access App Control](/defender-cloud-apps/proxy-intro-aad)

We've also covered these steps in [Step 2. Create Defender for Cloud Apps policies](create-policies.md).



## Apply sensitivity labels to SaaS apps
After discovering and classifying sensitive information, you need to apply sensitivity labels on them so that appropriate action can be applied to protect files. For example, a file that is labeled "Confidential" may be encrypted and have a "Confidential" watermark applied to it.


Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services. So when you want to define sensitive information, head over to the Microsoft Purview Information Protection portal to create them, and once defined they will be available in Defender for Cloud Apps.

For more information, see [Apply Microsoft Information Protection labels automatically](/defender-cloud-apps/use-case-information-protection).


## Extend DLP policies to SaaS apps

For apps with connectors, 


You can scope DLP policies to Microsoft Defender for Cloud Apps to monitor, detect and take actions when sensitive items are used and shared via non-Microsoft cloud apps.

For more information, see [Use data loss prevention policies for non-Microsoft cloud apps](/microsoft-365/compliance/dlp-use-policies-non-microsoft-cloud-apps).