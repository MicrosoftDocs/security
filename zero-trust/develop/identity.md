---
title: Building apps that secure identity through permissions and access
description: Learn about authentication, authorization, and identity management so that you can use a Zero Trust approach to identity in your software development lifecycle (SDLC).
ms.date: 09/12/2022
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.custom: template-concept
# Customer intent: As a developer, I want to learn about authentication, authorization, and identity management so that I can use a Zero Trust approach to identity in my software development lifecyle (SDLC).
---
# Building apps that secure identity through permissions and consent

This article continues from the [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) article to help you use a Zero Trust approach to identity in your software development lifecycle (SDLC). Below, you'll find an overview of the **Permissions and access** articles in this [Developer Guide](overview.md) so that you can dive into identity components that include authentication, authorization, and identity management.

- [Integrating applications with Azure AD and the Microsoft identity platform](integrate-apps-with-azure-ad-microsoft-identity-platform.md) helps developers to build and integrate apps that IT pros can secure in the enterprise by securely integrate apps with Azure Active Directory (Azure AD) and the Microsoft identity platform.
- [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts.
- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Securing applications with Continuous Access Evaluation](secure-with-cae.md) helps developers to improve application security with Continuous Access Evaluation. Learn how to [ensure Zero Trust support](overview.md) in your apps that receive authorization to access resources when they acquire access tokens from Azure Active Directory (Azure AD).
- [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
- [Requesting permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience when application permissions will require administrative consent.
- [Reducing overprivileged permissions and apps](overprivileged-permissions.md) helps you to understand why applications shouldn't request more permissions than they need (overprivileged) and how to limit privilege to manage access and improve security.
- [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Example of API protected by Microsoft identity consent framework](protected-api-example.md) helps you to design least privilege application permissions strategies for the best user experience.
- [Calling an API from another API](api-calls-api.md) helps you to ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.

## Next steps

- [Subscribe](/api/search/rss?search=%22Develop+using+Zero+Trust+principles%22&locale=en-us) to  our *Develop using Zero Trust principles* RSS feed for notification of new articles.
- [Develop using Zero Trust principles](overview.md) helps you to understand the guiding principles of Zero Trust so that you can improve your application security.
- [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.
- [Build Zero Trust-ready apps using Microsoft identity platform features and tools](/azure/active-directory/develop/zero-trust-for-developers) maps features of the Microsoft identity platform to the principles of Zero Trust.
- The [Identity integrations](../integrate/identity.md) guide explains how to integrate security solutions with Microsoft products to create Zero Trust solutions.
