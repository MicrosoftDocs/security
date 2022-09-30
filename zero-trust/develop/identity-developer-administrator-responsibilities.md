---
title: Developer and administrator responsibilities
description: As a developer creating applications in the Microsoft identity platform, knowing what your IT Pros need from you, and what you need from them, will help you to streamline your zero-trust development workflow.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 09/15/2022
ms.custom: template-concept
# Customer intent: As a developer creating applications in the Microsoft identity platform, I want to know what my IT Pros need from me, and what I need from them, so that I can streamline my zero-trust development workflow.
---
# Developer and administrator responsibilities for application registration,  authorization, and access

As a developer creating applications in the Microsoft identity platform, you'll work with IT Professionals who have administrator privileges in Azure Active Directory (AD) to enable your applications to take full advantage of the Microsoft identity platform. Knowing what your IT Pros need from you, and what you need from them, will help you to streamline your zero-trust development workflow.

## Developers and IT Pros must work together

IT organizations are increasingly blocking apps with vulnerabilities. As IT departments embrace a [Zero Trust approach](overview.md), developers who don't provide applications that follow Zero Trust principles risk not having their apps adopted. Following Zero Trust principles can help ensure that your application is eligible for adoption in a Zero Trust world.

App developers will usually implement, evaluate, and validate aspects of Zero Trust before working with an organization's IT Pros to achieve full compliance and adherence. Developers are responsible for building and integrating apps so that IT Pros can use their tools to further secure the applications. Partnering with IT Pros can help to

* minimize the probability of or prevent security compromise.
* quickly respond to compromise and reduce damage.

The following table summarizes the decisions and tasks required for developer and IT Pro roles to build and deploy secure applications in the Microsoft identity platform. Read on for key details and links to articles to help you plan your secure application development.

:::row:::
   :::column span="":::
      **Developer**
      - [Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app)
      - [Register an application with Azure AD and create a service principal](/azure/active-directory/develop/howto-create-service-principal-portal#register-an-application-with-azure-ad-and-create-a-service-principal)
      - [Define supported account types](identity-supported-account-types.md)
      - Is the app working on behalf of [itself](identity-non-user-applications.md) or the user
      - [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
   :::column-end:::
   :::column span="":::
      **IT Pro Administrator**
      - Who can register apps in a tenant
      - Application user, group, and role assignments
      - Permissions granted to an application
      - Policies including conditional access policy and token lifespan
      - Alternate local settings for an application
   :::column-end:::
:::row-end:::

## Zero Trust considerations

When entities (individuals, applications, devices) need to access resources in your application, you'll work with IT Pros who have administrator privileges to look at Zero Trust and security policy enforcement options and decide which policies to implement and enforce for access. Microsoft's policy enforcement engine needs to be in touch with things like threat intelligence, signal processing, and the policies that are already in place for the organization. Every time an entity needs to access a resource, it will go through the policy enforcement engine.

IT Pros determine which conditional access policies will apply to your application (SAML) or the resources your application is accessing (OAuth 2.0). They can apply conditional access policies to Security Assertions Markup Language (SAML) apps at authentication. For OAuth 2.0 applications, they can apply policies when an application attempts to access a resource.

## Next steps

* [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides an overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
* Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md).
* [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
