---
title: Develop using Zero Trust principles
description: As a developer, learn how to implement the guiding principles of Zero Trust so that you can improve your application security.
ms.date: 09/15/2022
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
# Customer intent: As a developer, I want to learn how to implement the guiding principles of Zero Trust so that I can improve your application security.
---
# Develop using Zero Trust principles

This article will help you, as a developer, to understand the guiding principles of Zero Trust so that you can improve your application security. You play a key role in organizational security; applications and their developers can no longer assume that the network perimeter is secure. Compromised applications can impact the entire organization.

Today, organizations are deploying new security models that adapt to complex modern environments and embrace the mobile workforce to protect people, devices, applications, and data wherever they're located. They are striving to achieve [Zero Trust](../zero-trust-overview.md), a security strategy and approach (not a product or a service) for designing and implementing applications that follow these guiding principles:

* Verify explicitly
* Use least privilege access
* Assume breach

Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model requires us to "never trust, always verify."

Understand that Zero Trust isn't a replacement for security fundamentals. With work originating from anywhere on any device, design your applications to incorporate Zero Trust principles throughout your development cycle.

## Why develop with a Zero Trust perspective?

* We've seen a rise in the level of sophistication of cybersecurity attacks.
* The "work from anywhere" workforce has redefined the security perimeter. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors.
* Corporate applications and data are moving from on-premises to hybrid and cloud environments. Traditional network controls can no longer be relied on for security. Controls need to move to where the data is: on devices and inside apps.

The development guidance in this section will help you to increase security, reduce the blast radius of a security incident, and swiftly recover by using Microsoft technology.

## Next steps

* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
* Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md).
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to understand what your IT Pros need from you, and what your need from them, so that you can streamline your zero-trust development workflow.
* [Building apps with a Zero Trust approach to identity](identity.md) continues from the [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) article to help you use a Zero Trust approach to identity in your software development lifecyle (SDLC).
* [Supported identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) explains how you can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts by configuring your app to be either single tenant or multitenant during app registration in Azure and ensure the Zero Trust principle of least privilege access so that your app only requests permissions it needs.
* [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application. To access protected resources like email or calendar data, your application needs the resource owner's authorization.
* [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
* [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management when you use the Microsoft identity platform to authenticate and authorize your applications and manage permissions and consent.
* [Requesting permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience for a scenario where you're writing your application code to request application permissions that will require administrative consent.
* When you're building non-user applications, you don't have a user whom you can prompt for a username and password or Multifactor Authentication (MFA). You need to provide the application's identity on its own. [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
* [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
* The demonstrations in [Example of API protected by Microsoft identity consent framework](protected-api-example.md) help you to design your application permissions strategy to provide the best experience for your users and tenant admins when you implement the Zero Trust principle of least privilege.
