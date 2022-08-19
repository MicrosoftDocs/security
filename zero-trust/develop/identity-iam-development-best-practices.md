---
title: Zero Trust identity and access management development best practices
description: To create secure applications that follow Zero Trust principles, Microsoft recommends that you incorporate best practices throughout your application development lifecycle.
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 08/18/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand best practices for my application development lifecycle so that I can create secure applications that follow Zero Trust principles.
---
# Zero Trust identity and access management development best practices

This article will help you, as a developer, to understand best practices for your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md). Customers are adopting Zero Trust principles, starting with identity and access management (IAM). While Zero Trust implementation continues to evolve, each organization's journey is unique and many begin with user and application identity.

Here are policies and controls that organizations prioritize as they roll out Zero Trust:

1. **Credential hygiene and rotation policies.** Secrets such as certificates or passwords are important assets to secure because, when compromised, they allow an attacker to move deeper within the system.
1. **Strong authentication.** IT administrators expect to be able to configure policies requiring multi-factor authentication.
1. **Restricting consent to apps with low-risk permissions to verified publishers.** While access to data in APIs like Microsoft Graph allow you to build rich applications, your organizations and customers will evaluate your app's permission requests and trustworthiness.
1. **Blocking legacy protocols and APIs.** This includes blocking older authentication protocols such as "Basic authentication" and requiring modern protocols like OpenID Connect and OAuth2. Organizations want to ensure the applications they depend upon are prepared.

## IAM best practices for Zero Trust application development

To create secure applications that follow Zero Trust principles, Microsoft recommends that you incorporate these best practices throughout your application development lifecycle.

### Use Microsoft Authentication Library (MSAL) and Microsoft Graph

Developing your application by following known and accepted standards and libraries increases application portability and security. [MSAL](/azure/active-directory/develop/msal-overview) and [Microsoft Graph](/graph/overview) are the best choices when developing an Azure Active Directory (AD) application.

Microsoft highly recommends that you develop your application using libraries such as MSAL rather than protocols because protocols have flaws, and their documentation can be extensive. MSAL developers have done the work for you with respect to compliance with protocols and MSAL is optimized for efficiency when working directly with Azure AD.

### Delegate Identity and Access Management

Develop your application to use tokens for explicit identity verification and access control that can be defined and managed by your customer. Microsoft does not recommend that you create your own username and password management system for your application.

### Plan for least privilege access policies

Zero Trust dictates that customers implement least privilege access. Your application must be developed and documented sufficiently that these policies can be configured successfully, meaning that your application must support tokens, and all APIs and resources that your application will call must be understood and documented.

### Manage tokens

Your application will request tokens from Azure AD. Managing these tokens involves verifying they are valid and scoped to your application, caching them appropriately, and using them as intended. Microsoft recommends that you handle token issues by checking for error classes and coding appropriate responses. Note that you should not read access tokens directly. Instead, use Microsoft identity platform best practices application to view access token scope and details under token response.

## Next steps

* The [Identity integrations](../integrate/identity.md) guide explains how independent software vendors and technology partners can integrate their security solutions with Microsoft products to create Zero Trust solutions for customers.
* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to understand what your IT Pros need from your, and what your need from them, so that your can streamline your zero-trust development workflow.
* [Building apps with a Zero Trust approach to identity](identity.md) helps you to use a Zero Trust approach to identity, which includes authentication, authorization, and identity management.
* [Identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) helps you to determine which users your app allows, during app registration, from single tenants and multi-tenants.
* [Providing application identity credentials when there is no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure Resources.
