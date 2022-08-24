---
title: Using standards-based development methodologies
description: In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform, along with links to more detailed articles. 
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 06/27/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to know about the benefits of using supported standards with MSAL in the Microsoft identity platform, so that I can have the most efficient and effective way to achieve Zero Trust.
---
# Using standards-based development methodologies

Making good use of industry standards for software development, augmented by the Microsoft Authentication Library (MSAL), ensures that your cloud applications meet Zero Trust requirements for optimal security. In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform, along with links to more detailed articles.

## What about protocols?

Implementing protocols should be left to very specific people and organizations who are willing to take on costs involved: the time it takes to write a first pass that is fully up to date with all best practices (following the many pages in the OAuth 2.0 best practices guide to develop secure implementation to properly implement the protocol). Instead, we firmly recommend that you use a well-maintained library with a preference for MSAL when you're building directly to Azure AD or Microsoft identity.

Our MSALs are optimized to build and to work with Azure AD. If you're in an environment where you have not implemented MSAL or that has very specific capabilities that are unlocked by its own library, the easiest, most efficient way to develop your application using the Microsoft identity platform is to build on OAuth 2.0 capabilities and OpenID Connect. The third choice is to fall back to a protocol but be aware of the costs that you're taking on to correctly do so.

Continue reading this article for an overview of supported standards and MSAL benefits (with links to more detailed articles) so that you can learn how to use them in developing your Zero Trust applications.

## How the Microsoft identity platform supports standards

When you develop your applications with the following industry standards that the Microsoft identity platform supports, you have the most efficient and effective way to achieve Zero Trust.

- OAuth 2.0
- SAML

### OAuth 2.0

As the industry protocol for authorization, OAuth 2.0 allows a user to grant limited access to its protected resources. Working with Hypertext Transfer Protocol (HTTP), OAuth 2.0 separates the client role from the resource owner. Clients use tokens to access protected resources on a resource server.

### Security Assertions Markup Language (SAML)

The Microsoft identity platform uses SAML 2.0 to enable your Zero Trust applications to provide a single sign-on (SSO) experience to your users. SSO and Single Sign-Out SAML profiles in Azure Active Directory (Azure AD) explain how the identity provider service uses SAML assertions, protocols, and bindings. The SAML protocol requires the identity provider (Microsoft identity platform) and the service provider (your application) to exchange information about themselves. When you register your zero-trust application with Azure AD, you register federation-related information that includes the Redirect URI and Metadata URI of the application with Azure AD.

## Benefits of MSAL over protocols

We optimize our MSALs for the Microsoft identity platform and provide the best experience for SSO, token caching, and outage resilience. We have a variety of MSALs that are generally available and coverage of our languages and frameworks continues to expand.

Using MSAL, you can acquire tokens for application types that include web applications, web APIs, single page apps, mobile and native applications, daemons, and server-side applications. MSAL enables fast and simple integration with secure access to users and data made simple via Microsoft Graph, other APIs, and your own APIs. With best-in-class auth libs, you can reach any audience and follow the Microsoft Security Development Lifecycle.

## Next steps

- [How the Microsoft identity platform uses the SAML protocol - Microsoft Entra | Microsoft Docs](/azure/active-directory/develop/active-directory-saml-protocol-reference) explains how to enable applications to provide a single sign-on (SSO) experience to your users.
- [Microsoft identity platform authentication libraries - Microsoft Entra | Microsoft Docs](/azure/active-directory/develop/reference-v2-libraries) shows Microsoft Authentication Library support for several application types with links to library source code, where to get the package for your app's project, and whether the library supports user sign-in (authentication), access to protected web APIs (authorization), or both.
- [OAuth 2.0 and OpenID Connect protocols on the Microsoft identity platform - Microsoft Entra | Microsoft Docs](/azure/active-directory/develop/active-directory-v2-protocols) provides some basic protocol terms and concepts to make your integration and debugging tasks easier.
