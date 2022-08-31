---
title: Using standards-based development methodologies
description: In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform, along with links to more detailed articles. 
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 08/31/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to know about the benefits of using supported standards with MSAL in the Microsoft identity platform, so that I can have the most efficient and effective way to achieve Zero Trust.
---
# Using standards-based development methodologies

Making good use of industry standards for software development, augmented by the [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) (MSAL), ensures that your cloud applications meet Zero Trust requirements for optimal security. In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the [Microsoft identity platform](/azure/active-directory/develop/v2-overview).

## What about protocols?

Implementing protocols should be left to very specific people and organizations who are willing to take on costs involved: the time it takes to write a first pass that is fully up to date with all best practices (following the many pages in the OAuth 2.0 best practices guide to develop secure implementation to properly implement the protocol). Instead, we firmly recommend that you use a well-maintained library with a preference for MSAL when you're building directly to Azure AD or Microsoft identity.

Our MSALs are optimized to build and to work with Azure AD. If you're in an environment where you have not implemented MSAL or that has very specific capabilities that are unlocked by its own library, the easiest, most efficient way to develop your application using the Microsoft identity platform is to build on OAuth 2.0 capabilities and OpenID Connect. The third choice is to fall back to a protocol but be aware of the costs that you're taking on to correctly do so.

Continue reading this article for an overview of supported standards and MSAL benefits (with links to more detailed articles) so that you can learn how to use them in developing your Zero Trust applications.

## How the Microsoft identity platform supports standards

When you develop your applications with the following industry standards that the Microsoft identity platform supports, you have the most efficient and effective way to achieve Zero Trust.

- [OAuth 2.0 and OpenID Connect](/azure/active-directory/develop/active-directory-v2-protocols)
- [SAML](/azure/active-directory/develop/active-directory-saml-protocol-reference)

### OAuth 2.0 and OpenID Connect

As the industry protocol for authorization, OAuth 2.0 allows a user to grant limited access to its protected resources. Working with Hypertext Transfer Protocol (HTTP), OAuth 2.0 separates the client role from the resource owner. Clients use tokens to access protected resources on a resource server.

OpenID Connect constructs allow Azure AD extensions to enhance security, the most used of which include the following.

- Azure AD can use [Conditional Access (CA)](/azure/active-directory/conditional-access/overview) to bring signals together, make access decisions, and enforce organizational policies. These policies ensure that a user meets specific criteria to access an application. Criteria can include requiring a managed device, accessing from a specific location, blocking a specific location, and configuring attributes like group membership. Conditional Access can redirect the user back to the identity provider for multi-factor authentication or to meet requirements such as password changes.
- [Conditional Access authentication context](/azure/active-directory/develop/developer-guide-conditional-access-authentication-context) allows apps to apply granular policies to protect sensitive data and actions instead of just at the app level.
- [Continuous Access Evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) enables Azure AD applications to subscribe to critical events that can then be evaluated and enforced. This includes evaluation of events such as user accounts being disabled or deleted, password changes, token revocations, and users detected as being risky.

Your applications that use enhanced security features like CAE and Conditional Access authentication context must include code to handle claims challenges. Open protocols enable you to use claims challenges and claims requests to invoke additional client capabilities such as indicating to apps that they need to re-interact with Azure AD (e.g., in case of an anomaly or if the user no longer satisfies conditions under which they had earlier authenticated). You can code for these extensions without disturbing primary authentication code flows.

### Security Assertions Markup Language (SAML)

The Microsoft identity platform uses SAML 2.0 to enable your Zero Trust applications to provide a single sign-on (SSO) experience to your users. SSO and Single Sign-Out SAML profiles in Azure Active Directory (Azure AD) explain how the identity provider service uses SAML assertions, protocols, and bindings. The SAML protocol requires the identity provider (Microsoft identity platform) and the service provider (your application) to exchange information about themselves. When you register your zero-trust application with Azure AD, you register federation-related information that includes the Redirect URI and Metadata URI of the application with Azure AD.

## Benefits of MSAL over protocols

Microsoft optimizes MSALs for the Microsoft identity platform and provides the best experience for SSO, token caching, and outage resilience. A variety of MSALs are generally available and coverage of our languages and frameworks continues to expand.

Using MSAL, you can acquire tokens for application types that include web applications, web APIs, single page apps, mobile and native applications, daemons, and server-side applications. MSAL enables fast and simple integration with secure access to users and data made simple via Microsoft Graph, other APIs, and your own APIs. With best-in-class auth libs, you can reach any audience and follow the Microsoft Security Development Lifecycle.

## Next steps

- [Microsoft identity platform authentication libraries](/azure/active-directory/develop/reference-v2-libraries) provides MSAL support for several application types with links to library source code, where to get the package for your app's project, and whether the library supports user sign-in (authentication), access to protected web APIs (authorization), or both.
- [Develop using Zero Trust principles](overview.md) will help you, as a developer, to understand the guiding principles of Zero Trust so that you can improve your application security.
- [What do we mean by Zero Trust compliance?](identity-zero-trust-compliance.md) provides overview of application security from a developer's perspective to address the guiding principles of Zero Trust.
- [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) will help you to understand best practices for your application development lifecycle so that you can create secure applications that are Zero Trust compliant.
- [Using standards-based development methodologies](identity-standards-based-development-methodologies.md) provides an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to understand what your IT Pros need from your, and what your need from them, so that your can streamline your zero-trust development workflow.
- [Building apps with a Zero Trust approach to identity](identity.md) helps you to use a Zero Trust approach to identity, which includes authentication, authorization, and identity management.
