---
title: What do we mean by Zero Trust compliance?
description: In this article, we provide an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 06/27/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand application security so that I can address the guiding principles of Zero Trust.
---
# What do we mean by Zero Trust compliance?

While security has been a talking point for decades, the ability to ensure your applications are as secure as possible is an important requirement from your customer's perspective. Cybersecurity is of utmost importance to customers and governments worldwide, and compliance with cybersecurity requirements is a prerequisite for many customers and governments to purchase applications. For example, see [U.S. Executive Order 14028: Improving the Nation's Cybersecurity](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/) and [U.S. General Services Administration requirements summary](https://www.gsa.gov/technology/technology-products-services/it-security/executive-order-14028-improving-the-nations-cybersecurity). If your application does not meet customer requirements, customers will not purchase your application.

What do we mean when we talk about application security from a developer perspective? The Zero Trust approach to application security means that an application has been developed to address the [guiding principles of Zero Trust](../zero-trust-overview.md). As a developer, you will need to continuously update your application as the threat landscape and security guidance changes.

## What do you need in your code to support Zero Trust principles?

At a fundamental level, two of the keys to your application's compliance with Zero Trust principles are the ability of your application to verify explicitly and to support least privilege access. To achieve this, your application should delegate identity and access management to Azure Active Directory (AD), enabling your application to use Azure AD tokens. Delegating identity and access management enables your application to support technologies that your customer implements such as multi-factor authentication, passwordless authentication, and conditional access policies. With Microsoft's identity platform, using Azure AD tokens enables your application to integrate with Microsoft's entire suite of security technologies.

:::image type="content" source="../media/diagram-microsoft-zero-trust-enabling-technologies.png" alt-text="diagram shows the technologies that enable Microsoft Zero Trust; at the center is Azure AD Conditional Access policy enforcement" lightbox="../media/diagram-microsoft-zero-trust-enabling-technologies.png":::

> [!NOTE]
> If your application requires passwords, you may be exposing your customers to avoidable risk. Bad actors view the shift to working from any location with any device as an opportunity to access corporate data by perpetrating activities such as password spray attacks. A password spray attack occurs when a bad actor chooses a promising password and tries that password across a set of user accounts. For example, they might try GoSeaHawks2022! against user accounts in the Seattle area. This type of attack has been successful and is one reason for the movement in cybersecurity towards passwordless authentication.

## Acquiring access tokens from Azure AD

At a minimum, your application needs to support acquiring access tokens from Azure AD. This is an OAuth 2.0 access token that is issued by Azure AD that a client application can use to obtain limited access to a user's resources via API calls on the user's behalf. You need an access token to call each API.

Because identity is verified by using a delegated identity provider, your customer's IT department can configure Azure AD to automatically enforce least privilege access by using [Conditional Access policies](/azure/active-directory/conditional-access/overview). Azure AD will use information in access tokens to manage token validation according to these policies.

> [!NOTE]
> Ensure that your customers understand all corporate resources that your application needs to access so that they can correctly define their policies. For example, if your application needs to access Microsoft SharePoint, include this information in your documentation so that you can help your customer to minimize policy conflicts.
