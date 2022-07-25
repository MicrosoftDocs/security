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

This solution builds on the Microsoft Information Protection solution guidance and guides you on how to use Defender for Cloud App to extend information protection to data in SaaS apps.


Microsoft Purview Information Protection helps you discover, classify, and protect sensitive information wherever it lives or travels. These information protection capabilities give you the tools to know your data, protect your data, and prevent data loss.

:::image type="content" source="media/saas-information-protection-flow.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365" lightbox="media/saas-information-protection-flow.png":::


:::image type="content" source="media/information-protection-saas-flow.png" alt-text="Image of how to deploy information protection on SaaS apps using Microsoft 365" lightbox="media/information-protection-saas-flow.png":::


To know your data you must identify and classify your data. To identify your data, you need to define what is considered to be sensitive information for your organization. Define sensitive information using the Microsoft Purview Information Protection portal to create sensitive types and labels, and once defined they will be available in Defender for Cloud Apps.


Defender for Cloud Apps is natively integrated with Microsoft Purview Information Protection and the same sensitive types and labels are available throughout both services. You can also use advanced classifications types such as fingerprint or Exact Data Match (EDM).






After identifying and classifying your data, you can then proceed to protect your data. You can apply protection actions that such as encryption, access restrictions, and other actions. Capabilities such as sensitivity labels lets you classify data across your organization, and enforce protection settings based on that classification. That protection then stays with the content.







Use the following steps to guide you in using Microsoft 365 products so that you can apply information protection capabilities on SaaS apps:


|Step  |Description  |
|---------|---------|
|1     |  Hone sensitive information types. For more information, see [Learn about Sensitive information types](/microsoft-365/compliance/sensitive-information-type-learn-about).        |
|2     |      |
|3     |      |


Steps:

- Hone sensitive information types in Microsoft 365 data (MS Purview)
- Create classification schema and labels 
- Use Defender for Cloud Apps discovery to discover sensitive data using the honed sensitive information types (From MS Info Prot Purview -- to Defender for Cloud apps)
- Define sensitivity labels ( Microsoft Purview compliance portal)
- Use Defender for Cloud Apps to extend labels out to SaaS apps
- Define DLP policies in Microsft 365
- Use Defender for Cloud Apps to extend Microsoft 365 DLP to SaaS apps





## Discover and classify sensitive information in SaaS apps




## Apply sensitivity labels to SaaS apps




## Extend DLP policies to cloud apps

