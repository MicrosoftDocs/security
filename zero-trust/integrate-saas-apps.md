---
title: Integrate SaaS apps for Zero Trust with Microsoft 365
description: Learn how to integrate SaaS apps for Zero Trust with Microsoft 365
ms.date: 06/08/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Integrate SaaS apps for Zero Trust with Microsoft 365 overview


The widespread adoption of remote work has created a shift in the way people access corporate resources. This shift highlights the reliance of organizations on cloud-based apps to ensure business continuity. Software-as-a-service (SaaS)  plays a key role in ensuring that applications and resources are available and accessible from any device with an Internet connection.

While SaaS apps can provide this convenience, the large amount of sensitive data and the flexibility it affords users can also potentially pose a security risk.  

To ensure that access and productivity is secure, implementation of SaaS needs to align with the Zero Trust security model which is based on these guiding principles:

- Verify explicitly

    Always authenticate and authorize based on all available data points. This is where Zero Trust identity and device access policies are crucial to sign-in and ongoing validation.

- Use least privilege access

    Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.

- Assume breach

    Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

## Implementing the layers of protection for SaaS apps

Protecting SaaS apps is a multi-layer process. 


The following diagram illustrates building blocks to integrate SaaS apps that aligns with the Zero Trust security model. The elements related to achieving this are numbered 3, 10, and 13. These are the layers of protection device admins will coordinate with other administrators to accomplish.


:::image type="content" source="media/saas-zt.png" alt-text="Image of Zero Trust deployment guidance" lightbox="media/saas-zt.png":::

In this illustration:


|&nbsp;|Step|Description|Licensing requirements|
|---|---|---|---|
|3|Add SaaS apps to Azure Active Directory ||E3, E5, F1, F3, F5|
|10|Create Defender for Cloud apps policies ||E3, E5, F1, F3, F5|
|13|Deploy information protection for SaaS apps ||E3, E5, F3, F5|



For more information, see the [Microsoft 365 Zero Trust deployment plan](/microsoft-365/security/microsoft-365-zero-trust).


## What's in this solution
This solution steps through the deployment of key layers to integrate SaaS apps for Zero Trust with Microsoft 365. 

Microsoft 365 helps you manage your SaaS applications giving you control and optics to discover and manage apps. You are likely already aware of the primary cloud apps used by your organization. Azure AD includes a gallery of apps you can add to your directory. You can also use Defender for Cloud App to discover additional cloud your users interact with. 


:::image type="content" source="media/saas-zt-steps.png" alt-text="Image of Zero Trust SaaS guidance" :::


The steps in this solutions are:
1. [Add SaaS apps in Azure Active Directory]().
2. [Create Defender for Cloud Apps policies]().
3. [Deploy information protection for SaaS apps]().




|&nbsp;|Step|Description|Licensing requirements|
|---|---|---|---|
|3|Add SaaS apps to Azure Active Directory ||E3, E5, F1, F3, F5|
|10|Create Defender for Cloud apps policies ||E3, E5, F1, F3, F5|
|13|Deploy information protection for SaaS apps ||E3, E5, F3, F5|

