---
title: Develop using Zero Trust principles
description: As a developer, learn how to implement the the guiding principles of Zero Trust so that you can improve your application security.
ms.date: 08/31/2022
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
---

# Develop using Zero Trust principles

This article will help you, as a developer, to understand the guiding principles of Zero Trust so that you can improve your application security. You play a key role in organizational security; applications and their developers can no longer assume that the network perimeter is secure. Compromised applications can impact the entire organization.

Today, organizations are deploying new security models that effectively adapt to the complexity of the modern environment, embrace the mobile workforce, and protect people, devices, applications, and data wherever they are located. This is the core of [Zero Trust](../zero-trust-overview.md), a security strategy and approach (not a product or a service) for designing and implementing applications with these guiding principles:

* Verify explicitly
* Use least privilege access
* Assume breach

Instead of believing everything behind the corporate firewall is safe, the Zero Trust model assumes breach and verifies each request as though it originated from an uncontrolled network. Regardless of where the request originates or what resource it accesses, the Zero Trust model requires us to "never trust, always verify."

While Zero Trust is not a replacement for security fundamentals, with work originating from anywhere on any device, it is essential that you design your applications to incorporate Zero Trust principles throughout your development cycle.

## Why develop with a Zero Trust perspective?

* We've seen a rise in the level of sophistication of cybersecurity attacks.
* The "work from anywhere" workforce has redefined the security perimeter. Data is being accessed outside the corporate network and shared with external collaborators such as partners and vendors.
* Corporate applications and data are moving from on-premises to hybrid and cloud environments. Traditional network controls can no longer be relied on for security. Controls need to move to where the data is: on devices and inside apps.

The development guidance in this section will help you to increase security, reduce the blast radius of a security incident, and swiftly recover by leveraging Microsoft technology.

## Next steps

* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
* [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) will help you to understand best practices for your application development lifecycle so that you can create secure applications that are Zero Trust compliant.
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
* [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to understand what your IT Pros need from your, and what your need from them, so that your can streamline your zero-trust development workflow.
* [Building apps with a Zero Trust approach to identity](identity.md) helps you to use a Zero Trust approach to identity, which includes authentication, authorization, and identity management.
* [Identity and account types for single- and multi-tenant apps](identity-supported-account-types.md) helps you to determine which users your app allows, during app registration, from single tenants and multi-tenants.
* [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
* [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application.
* [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to determine your application permission approach to credential management.
* [Providing application identity credentials when there is no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure Resources.
* [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
