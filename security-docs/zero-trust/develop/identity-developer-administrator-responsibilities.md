---
title: Developer and administrator responsibilities
description: Learn what IT Pros need from developers and what developers need from them to streamline Zero Trust development workflows.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 02/24/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer creating applications in the Microsoft identity platform, I want to know what my IT Pros need from me, and what I need from them, so that I can streamline my Zero Trust development workflow.
---
# Developer and administrator responsibilities for application registration, authorization, and access

When you create applications in the Microsoft identity platform, work with IT Professionals who have administrator privileges in Microsoft Entra ID to enable your applications to take full advantage of the Microsoft identity platform. Know what your IT Pros need from you and what you need from them to streamline your Zero Trust development workflow.

## Developers and IT Pros must work together

IT organizations increasingly block apps with vulnerabilities. As IT departments embrace a [Zero Trust approach](overview.md), developers who don't provide applications that follow Zero Trust principles risk not having their apps adopted. Following Zero Trust principles can help ensure that your application is eligible for adoption in a Zero Trust environment.

App developers usually implement, evaluate, and validate aspects of Zero Trust before working with an organization's IT Pros to achieve full compliance and adherence. Developers are responsible for building and integrating apps so that IT Pros can use their tools to further secure the applications. Partner with IT Pros so that you can:

- Minimize the probability of or prevent security compromise.
- Quickly respond to compromise and reduce damage.

The following table summarizes the decisions and tasks required for developer and IT Pro roles to build and deploy secure applications in the Microsoft identity platform. Read on for key details and links to articles to help you plan your secure application development.

:::row:::
   :::column span="":::
      **Developer**
      - [Register app](/entra/identity-platform/quickstart-register-app) in Microsoft identity platform.
      - Define [supported account types](identity-supported-account-types.md).
      - Determine if app works on behalf of [itself](identity-non-user-applications.md) or user.
      - Define [resources](acquire-application-authorization-to-access-resources.md) required and how/when to request permission.
   :::column-end:::
   :::column span="":::
      **IT Pro Administrator**
      - Configure who can register apps in tenant.
      - Assign application users, groups, and roles.
      - Grant permissions to applications.
      - Define policies, including conditional access policy.
   :::column-end:::
:::row-end:::

## Zero Trust considerations

When entities (individuals, applications, devices) need to access resources in your application, work with IT Pros and consider Zero Trust and security policy enforcement options. Together, decide which access policies to implement and enforce. Microsoft's policy enforcement engine needs to be in touch with threat intelligence, signal processing, and existing policies. Every time an entity needs to access a resource, it goes through the policy enforcement engine.

IT Pros can apply conditional access policies to Security Assertions Markup Language (SAML) apps at authentication. For OAuth 2.0 applications, they can apply policies when an application attempts to access a resource. IT Pros determine which conditional access policies apply to your application (SAML) or the resources that your application accesses (OAuth 2.0).

## Next steps

- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Configure group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles. These methods help to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards and their benefits.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
