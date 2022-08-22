---
title: What do we mean by Zero Trust compliance?
description: Get an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 08/18/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand application security so that I can address the guiding principles of Zero Trust.
---
# What do we mean by Zero Trust compliance?

This article provides overview of application security from a developer's perspective to address the guiding principles of [Zero Trust](overview.md). In the past, code security was all about your own app: if you got it wrong, your own app was at risk. While security has been a talking point for decades, the ability to ensure your applications are as secure as possible is an important requirement from your customer's perspective.

Cybersecurity is a high priority for customers and governments worldwide. Compliance with cybersecurity requirements is a prerequisite for many customers and governments to purchase applications. For example, see [U.S. Executive Order 14028: Improving the Nation's Cybersecurity](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/) and [U.S. General Services Administration requirements summary](https://www.gsa.gov/technology/technology-products-services/it-security/executive-order-14028-improving-the-nations-cybersecurity). If your application does not meet customer requirements, customers will not purchase your application.

Cloud security is about your company's infrastructure. The infrastructure is only as secure as the weakest link. A single app can be the weakest link that malicious actors can hijack to gain access to business-critical data and operations.

What do we mean when we talk about application security from a developer perspective? The Zero Trust approach to application security means that an application addresses the guiding principles of Zero Trust. As a developer, you will need to continuously update your application as the threat landscape and security guidance changes.

## Supporting Zero Trust principles in your code

At a fundamental level, two of the keys to your application's compliance with Zero Trust principles are the ability of your application to verify explicitly and to support least privilege access. To achieve this, your application should [delegate identity and access management](identity-iam-development-best-practices.md) to Azure Active Directory (AD), enabling your application to use Azure AD tokens. Delegating identity and access management enables your application to support technologies that your customer implements such as multi-factor authentication, passwordless authentication, and conditional access policies.

With the [Microsoft identity platform](/azure/active-directory/develop/v2-overview) and Zero Trust enabling technologies (as shown in the following diagram), using Azure AD tokens enables your application to integrate with Microsoft's entire suite of security technologies.

:::image type="content" source="../media/diagram-microsoft-zero-trust-enabling-technologies.png" alt-text="diagram shows the technologies that enable Microsoft Zero Trust; at the center is Azure AD Conditional Access policy enforcement" lightbox="../media/diagram-microsoft-zero-trust-enabling-technologies.png":::

If your application requires passwords, you may be exposing your customers to avoidable risk. Bad actors view the shift to working from any location with any device as an opportunity to access corporate data by perpetrating activities such as password spray attacks. A password spray attack occurs when a bad actor chooses a promising password and tries that password across a set of user accounts. For example, they might try GoSeaHawks2022! against user accounts in the Seattle area. This type of attack has been successful and is one reason for the movement in cybersecurity towards passwordless authentication.

## Acquiring access tokens from Azure AD

At a minimum, your application needs to support [acquiring access tokens](acquire-application-authorization-to-access-resources.md) from Azure AD. This is an OAuth 2.0 access token that is issued by Azure AD. Your client application can use these tokens to obtain limited access to user resources via API calls on the user's behalf. You'll need an access token to call each API.

Because identity is verified by using a delegated identity provider, your customer's IT department can configure Azure AD to automatically enforce least privilege access with [Conditional Access policies](/azure/active-directory/conditional-access/overview). Azure AD will use information in access tokens to manage token validation according to Azure AD tenant policies.

Ensure that your customers understand all corporate resources that your application needs to access so that they can correctly define their policies. For example, if your application needs to access Microsoft SharePoint, include this information in your documentation so that you can help your customer to minimize policy conflicts.

## Next steps

- [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
- [Building apps with a Zero Trust approach to identity](identity.md) helps you to use a Zero Trust approach to identity, which includes authentication, authorization, and identity management.
- [Identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) helps you to determine which users your app allows, during app registration, from single tenants and multi-tenants.
- [Providing application identity credentials when there is no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure Resources.
