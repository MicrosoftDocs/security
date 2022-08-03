---
title: Integrate SaaS apps for Zero Trust with Microsoft 365
description: Learn how to integrate SaaS apps for Zero Trust with Microsoft 365
ms.date: 06/06/2022
ms.service: security
author: mjcaparas
ms.author: macapara
ms.topic: conceptual
---

# Integrate SaaS apps for Zero Trust with Microsoft 365 

The widespread increase in cloud adoption is transforming how organizations achieve business outcomes.  This shift highlights the  reliance of companies on cloud-based apps resulting in higher demand for services such as Software as a service (SaaS), Platform as a service (PaaS), Infrastructure as a service (IaaS), and app development platforms. 


While a multicloud environment can help reduce operational costs and improve scalability, the large amount of sensitive data and the flexibility it affords organizations can potentially pose a security risk. Deliberate steps must be taken to ensure that resources hosted in the cloud are protected. 

This solution guides you on applying Zero Trust principles using Microsoft 365 to help manage your digital estate of cloud apps, with a focus on SaaS. SaaS apps play a key role in ensuring that applications and resources are available and accessible from any device with an Internet connection.

To ensure that access and productivity is secure, implementation of SaaS needs to align with the Zero Trust security model, which is based on these guiding principles:

- Verify explicitly

    Always authenticate and authorize based on all available data points. This is where Zero Trust identity and device access policies are crucial to sign-in and ongoing validation.

- Use least privileged access

    Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.

- Assume breach

    Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses.

Microsoft 365 capabilities help you bring your SaaS apps into management to meet the principles of Zero Trust security. 


:::image type="content" source="media/saas-apps-products.png" alt-text="Image of SaaS apps and Microsoft products":::

In the illustration:
- A collection of SaaS apps is pictured.
- You can add these SaaS apps to Azure Active Directory and include these apps in the scope of your multi-factor authentication and conditional access policies. For more information, [Integrating all your apps with Azure AD](/azure/active-directory/fundamentals/five-steps-to-full-application-integration-with-azure-ad).
- Using Microsoft Defender for Cloud Apps, you can discover other cloud apps your organization uses. You can approve apps and apply session controls. Of course, you can add newly discovered cloud apps to Azure AD to enforce multi-factor authentication and other policies.
- Microsoft Purview Information Protection capabilities can be extended out to these cloud apps to discover sensitive data, protect data, and prevent data loss.


## Implementing the layers of protection for SaaS apps

Protecting SaaS apps is a multi-layer process. 


The following diagram illustrates building blocks to integrate SaaS apps that align with the Zero Trust security model. The elements related to achieving this are numbered 1, 2, and 3. These are the layers of protection device admins will coordinate with other administrators to accomplish.


:::image type="content" source="media/saas-zt.png" alt-text="Image of Zero Trust deployment guidance" lightbox="media/saas-zt.png":::

In this illustration:


|&nbsp;|Step|Description|Licensing requirements|
|---|---|---|---|
|1|Add SaaS apps to Azure Active Directory |Add applications to Azure Active Directory (Azure AD) so that authorized users can securely access it. Many types of applications can be registered with Azure AD.| P1, P2 |
|2|Create Microsoft Defender for Cloud Apps policies |You want to make sure that policies are in place to ensure that only authorized users and specific conditions are met before users are able to access resources.   | A5, E5, F5|
|3|Deploy information protection for SaaS apps | Organizations need to protect proprietary information, ensure that information protection is in place so that sensitive data is protected.|E3, E5, F3, F5|



For more information, see the [Microsoft 365 Zero Trust deployment plan](/microsoft-365/security/microsoft-365-zero-trust).


## What's in this solution
This solution steps through the deployment of key layers to integrate SaaS apps for Zero Trust with Microsoft 365. 

Microsoft 365 helps you manage your SaaS applications giving you control and optics to discover and manage apps. You're likely already aware of the primary cloud apps used by your organization. Azure AD includes a gallery of apps you can add to your directory. You can also use Microsoft Defender for Cloud Apps to discover other cloud your users interact with. For more information, see [Discover and assess cloud apps](/defender-cloud-apps/best-practices#discover-and-assess-cloud-apps). After knowing your digital estate, you'll need to make sure that only authorized users and that certain conditions are met before they're accessed and that the information is properly protected.


:::image type="content" source="media/saas-zt-steps.png" alt-text="Image of Zero Trust SaaS guidance":::


The steps in this solutions are:
1. [Add SaaS apps in Azure Active Directory](add-saas-apps.md).
2. [Create Microsoft Defender for Cloud Apps policies]().
3. [Deploy information protection for SaaS apps]().


## Learning for administrators

The following resources help administrators learn concepts about SaaS. 

**[Design a strategy for securing PaaS, IaaS, and SaaS services](/learn/modules/design-strategy-for-secure-paas-iaas-saas-services/)**<br>
Description: Learn how to design a cybersecurity strategy, which will secure cloud services in the SaaS, PaaS, and IaaS service models.<br>
1 hr 42 min - 13 units

> [!div class="nextstepaction"]
> [Start >](/learn/modules/design-strategy-for-secure-paas-iaas-saas-services/)




