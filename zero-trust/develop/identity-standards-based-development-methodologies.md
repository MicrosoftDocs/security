---
title: Using standards-based development methodologies
description: In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform. 
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 06/20/2023
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to know about the benefits of using supported standards with MSAL in the Microsoft identity platform so that I can efficiently and effectively achieve Zero Trust.
---
# Using standards-based development methodologies

As a developer, you can make good use of industry standards for software development augmented by the [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) (MSAL). In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the [Microsoft identity platform](/azure/active-directory/develop/v2-overview). Ensure that your cloud applications meet Zero Trust requirements for optimal security.

## What about protocols?

When implementing protocols, consider costs that include time to write code that is fully up to date with all best practices and follows OAuth 2.0 best practices for secure implementation. Instead, we recommend that you use a well-maintained library (with a preference for MSAL) when you build directly to Microsoft Entra ID or Microsoft Identity.

We optimize MSALs to build and work with Microsoft Entra ID. If your environment hasn't implemented MSAL or has unlocked capabilities in its own library, develop your application with the Microsoft identity platform. Build on OAuth 2.0 capabilities and OpenID Connect. Consider costs of correctly falling back to a protocol.

## How the Microsoft identity platform supports standards

To achieve Zero Trust most efficiently and effectively, develop applications with industry standards that the Microsoft identity platform supports:

- [OAuth 2.0 and OpenID Connect](/azure/active-directory/develop/active-directory-v2-protocols)
- [SAML](/azure/active-directory/develop/active-directory-saml-protocol-reference)

### OAuth 2.0 and OpenID Connect

As the industry protocol for authorization, OAuth 2.0 allows users to grant limited access to protected resources. OAuth 2.0 works with Hypertext Transfer Protocol (HTTP) to separate the client role from the resource owner. Clients use tokens to access protected resources on a resource server.

OpenID Connect constructs allow Microsoft Entra extensions to enhance security. These Microsoft Entra extensions are the most common:

- [Conditional Access authentication context](/azure/active-directory/develop/developer-guide-conditional-access-authentication-context) allows apps to apply granular policies to protect sensitive data and actions instead of only at the app level.
- [Continuous Access Evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) enables Microsoft Entra applications to subscribe to critical events for evaluation and enforcement. CAE includes risky event evaluation such as disabled or deleted user accounts, password changes, token revocations, and detected users.

When your applications use enhanced security features like CAE and Conditional Access authentication context, they must include code to manage claims challenges. With open protocols, you use claims challenges and claims requests to invoke other client capabilities. For example, indicating to apps that they need to repeat interaction with Microsoft Entra ID due to an anomaly. Another scenario is when the user no longer satisfies conditions under which they had earlier authenticated. You can code for these extensions without disturbing primary authentication code flows.

### Security Assertions Markup Language (SAML)

The Microsoft identity platform uses SAML 2.0 to enable your Zero Trust applications to provide a single sign-on (SSO) user experience. SSO and Single Sign-Out SAML profiles in Microsoft Entra ID explain how the identity provider service uses SAML assertions, protocols, and bindings. The SAML protocol requires the identity provider (Microsoft identity platform) and the service provider (your application) to exchange information about themselves. When you register your Zero Trust application with Microsoft Entra ID, you register federation-related information that includes the Redirect URI and Metadata URI of the application with Microsoft Entra ID.

## Benefits of MSAL over protocols

Microsoft optimizes MSALs for the Microsoft identity platform and provides the best experience for SSO, token caching, and outage resilience. As MSALs are generally available, we continue to expand coverage of languages and frameworks.

Using MSAL, you acquire tokens for application types that include web applications, web APIs, single page apps, mobile and native applications, daemons, and server-side applications. MSAL enables fast and simple integration with secure access to users and data via Microsoft Graph and APIs. With best-in-class auth libs, you can reach any audience and follow the Microsoft Security Development Lifecycle.

## Next steps

- [Microsoft identity platform authentication libraries](/azure/active-directory/develop/reference-v2-libraries) describes application type support.
- [Develop using Zero Trust principles](overview.md) helps you to understand the guiding principles of Zero Trust so that you can improve your application security.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve Zero Trust goals.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how token customization improves flexibility and control while increasing application Zero Trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) describes how to configure apps with app role definitions and assign security groups to app roles. This approach improves flexibility and control while increasing application Zero Trust security with least privilege.
