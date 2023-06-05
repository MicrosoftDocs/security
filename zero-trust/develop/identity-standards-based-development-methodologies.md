---
title: Using standards-based development methodologies
description: In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the Microsoft identity platform, along with links to more detailed articles. 
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 06/29/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to know about the benefits of using supported standards with MSAL in the Microsoft identity platform, so that I can have the most efficient and effective way to achieve Zero Trust.
---
# Using standards-based development methodologies

Make good use of industry standards for software development, augmented by the [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) (MSAL). Ensure that your cloud applications meet Zero Trust requirements for optimal security. In this article, we provide an overview of supported standards (OAuth 2.0, OpenID Connect, SAML, WS-Federation, and SCIM) and the benefits of using them with MSAL and the [Microsoft identity platform](/azure/active-directory/develop/v2-overview).

## What about protocols?

Implementing protocols should be left to specific people and organizations who are willing to take on costs involved: the time it takes to write a first pass that is fully up to date with all best practices (following the many pages in the OAuth 2.0 best practices guide to develop secure implementation to properly implement the protocol). Instead, we firmly recommend that you use a well-maintained library with a preference for MSAL when you're building directly to Azure AD or Microsoft identity.

Our MSALs are optimized to build and to work with Azure AD. If your environment hasn't implemented MSAL or has unlocked capabilities in its own library, develop your application with the Microsoft identity platform. Build on OAuth 2.0 capabilities and OpenID Connect. Be aware of the costs that you're taking on to correctly fall back to a protocol.

Continue reading this article for an overview of supported standards and MSAL benefits and learn how to use them in Zero Trust applications development.

## How the Microsoft identity platform supports standards

Develop your applications with the following industry standards that the Microsoft identity platform supports to most efficiently and effectively achieve Zero Trust.

- [OAuth 2.0 and OpenID Connect](/azure/active-directory/develop/active-directory-v2-protocols)
- [SAML](/azure/active-directory/develop/active-directory-saml-protocol-reference)

### OAuth 2.0 and OpenID Connect

As the industry protocol for authorization, OAuth 2.0 allows a user to grant limited access to its protected resources. OAuth 2.0 works with Hypertext Transfer Protocol (HTTP) to separate the client role from the resource owner. Clients use tokens to access protected resources on a resource server.

OpenID Connect constructs allow Azure AD extensions to enhance security. The following are the most common Azure AD extensions:

- Azure AD can use [Conditional Access (CA)](/azure/active-directory/conditional-access/overview) to bring signals together, make access decisions, and enforce organizational policies. These policies ensure that a user meets specific criteria to access an application. Criteria can include requiring a managed device, accessing from a specific location, blocking a specific location, and configuring attributes like group membership. Conditional Access can redirect the user back to the identity provider for multi-factor authentication or to meet requirements such as password changes.
- [Conditional Access authentication context](/azure/active-directory/develop/developer-guide-conditional-access-authentication-context) allows apps to apply granular policies to protect sensitive data and actions instead of just at the app level.
- [Continuous Access Evaluation (CAE)](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) enables Azure AD applications to subscribe to critical events that can then be evaluated and enforced. CAE includes evaluation of events such as user accounts being disabled or deleted, password changes, token revocations, and users detected as being risky.

Your applications that use enhanced security features like CAE and Conditional Access authentication context must include code to handle claims challenges. Open protocols enable you to use claims challenges and claims requests to invoke other client capabilities. For example, indicating to apps that they need to repeat interaction with Azure AD due to anomaly or when the user no longer satisfies conditions under which they had earlier authenticated. You can code for these extensions without disturbing primary authentication code flows.

### Security Assertions Markup Language (SAML)

The Microsoft identity platform uses SAML 2.0 to enable your Zero Trust applications to provide a single sign-on (SSO) experience to your users. SSO and Single Sign-Out SAML profiles in Azure Active Directory (Azure AD) explain how the identity provider service uses SAML assertions, protocols, and bindings. The SAML protocol requires the identity provider (Microsoft identity platform) and the service provider (your application) to exchange information about themselves. When you register your zero-trust application with Azure AD, you register federation-related information that includes the Redirect URI and Metadata URI of the application with Azure AD.

## Benefits of MSAL over protocols

Microsoft optimizes MSALs for the Microsoft identity platform and provides the best experience for SSO, token caching, and outage resilience. Various MSALs are generally available and coverage of our languages and frameworks continues to expand.

Using MSAL, you can acquire tokens for application types that include web applications, web APIs, single page apps, mobile and native applications, daemons, and server-side applications. MSAL enables fast and simple integration with secure access to users and data made simple via Microsoft Graph, other APIs, and your own APIs. With best-in-class auth libs, you can reach any audience and follow the Microsoft Security Development Lifecycle.

## Next steps

- The [Microsoft identity platform authentication libraries](/azure/active-directory/develop/reference-v2-libraries) article provides MSAL support for several application types.
- [Develop using Zero Trust principles](overview.md) helps you to understand the guiding principles of Zero Trust so that you can improve your application security.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Developer and administrator responsibilities for application registration, authorization, and access](identity-developer-administrator-responsibilities.md) helps you to better collaborate with your IT Pros.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
