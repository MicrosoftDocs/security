---
title: What do we mean by Zero Trust compliance?
description: Get an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 02/24/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to understand application security so that I can address the guiding principles of Zero Trust.
---
# What do we mean by Zero Trust compliance?

This article provides overview of application security from a developer's perspective to address the guiding principles of [Zero Trust](overview.md). In the past, code security was all about your own app: if you got it wrong, your own app was at risk. Today, cybersecurity is a high priority for customers and governments worldwide.

Compliance with cybersecurity requirements is a prerequisite for many customers and governments to purchase applications. Your application needs to meet customer requirements.

Cloud security is a consideration of organization infrastructure that is only as secure as the weakest link. When a single app is the weakest link, bad actors can gain access to business-critical data and operations.

Application security from a developer perspective includes a Zero Trust approach: applications address the guiding principles of Zero Trust. As a developer, continuously update your application as the threat landscape and security guidance changes.

## Support Zero Trust principles in your code

Two keys to compliance with Zero Trust principles are the ability of your application to verify explicitly and to support least privilege access. Your application should [delegate identity and access management](identity-iam-development-best-practices.md) to Microsoft Entra ID so that it can use Microsoft Entra tokens. Delegating identity and access management enables your application to support customer technologies such as multifactor authentication, passwordless authentication, and conditional access policies.

With the [Microsoft identity platform](/entra/identity-platform/v2-overview) and Zero Trust enabling technologies, using Microsoft Entra tokens helps your application to integrate with Microsoft's entire suite of security technologies.

If your application requires passwords, you might be exposing your customers to avoidable risk. Bad actors view the shift to working from any location with any device as an opportunity to access corporate data by perpetrating activities such as password spray attacks. In a password spray attack, bad actors try a promising password across a set of user accounts. For example, they might try `GoSeaHawks2022!` against user accounts in the Seattle area. This successful attack type is one justification for passwordless authentication.

## Acquire access tokens from Microsoft Entra ID

At a minimum, your application needs to [acquire access tokens](acquire-application-authorization-to-access-resources.md) from Microsoft Entra ID that issues OAuth 2.0 access tokens. Your client application can use these tokens to obtain limited access to user resources via API calls on the user's behalf. You use an access token to call each API.

When a delegated identity provider verifies identity, your customer's IT department can enforce least privilege access with Microsoft Entra permission and consent. Microsoft Entra ID determines when it issues tokens to applications.

When your customers understand which corporate resources your application needs to access, they can correctly grant or deny access requests. For example, if your application needs to access Microsoft SharePoint, document this requirement so that you can help customers grant the correct permissions.

## Next steps

- [Standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards and their benefits.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. Learn how to customize tokens and improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Supported identity and account types for single- and multitenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Microsoft Entra tenant, any Microsoft Entra tenant, or users with personal Microsoft accounts.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
