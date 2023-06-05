---
title: Securing applications with Continuous Access Evaluation
description: As a developer, you can improve application security with Continuous Access Evaluation. In this article, you'll learn how to ensure Zero Trust support in your apps that receive authorization to access resources when they acquire access tokens from Azure Active Directory (Azure AD).
ms.date: 01/27/2023
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to improve application security with Continuous Access Evaluation. I want to learn how to ensure Zero Trust support in my apps that receive authorization to access resources when they acquire access tokens from Azure Active Directory (Azure AD).
---
# Securing applications with Continuous Access Evaluation

This article will help you, as a developer, to improve application security with Continuous Access Evaluation. You'll learn how to [ensure Zero Trust support](overview.md) in your apps that receive [authorization to access resources](acquire-application-authorization-to-access-resources.md) when they acquire access tokens from Azure Active Directory (Azure AD).

When Azure AD issues these access tokens, it fully evaluates the [conditions for that authorization](/azure/active-directory/conditional-access/overview). Azure AD performs standard authorization actions, such as [ensuring consent for the application has been granted](identity.md), every time it issues tokens for initial token requests and when it refreshes tokens.

Azure AD primarily uses JSON Web Tokens (JWT) for access tokens. A resource API can decode, validate, and interpret the JWT without needing to call back to Azure AD on every call to the resource API. The [JWT standard](https://www.rfc-editor.org/rfc/rfc7519) defines an exp claim that identifies the *on-or-after* expiration time that you must not accept the JWT token for processing. By default, Azure AD tokens expire 60 to 90 minutes after issue. Your applications must cache and use access tokens for this period during which Azure AD doesn't evaluate the authorization conditions.

## Evaluating conditions outside of issuing the token

Microsoft customers have expressed concerns about lags between user condition changes and policy change enforcement when Azure AD issues tokens. This reduced token lifetime approach can degrade user experiences and reliability without eliminating risks.

One solution is to evaluate conditions on every call to a protected resource. The most common way to implement this enforcement is token introspection. Token introspection doesn't use a JWT format for the token. Instead, token introspection uses an opaque string that the resource API can't interpret. The resource API sends the token to the identity provider on each call. The identity provider then checks for any conditions and returns data that the resource API can use to complete the operation. This process can be expensive as it adds another round trip web request to every API call.

To remedy this expense with [Continuous Access Evaluation](/azure/active-directory/conditional-access/concept-continuous-access-evaluation) (CAE), a resource API can listen for events that Azure AD pushes about the tokens that Azure AD issues for the resource API. For example, when your application calls the Microsoft Graph API, Microsoft Graph can check if it has received events from Azure AD about the token. If the conditions of the original authentication have changed and the user needs to reauthenticate, Microsoft Graph returns an error to the calling app.

Azure AD sends an event to CAE-enabled Microsoft resources when any of these events occur:

- Deleted or disabled user account
- Changed or reset user password
- Enabled user multi-factor authentication
- Administrator explicitly revokes all refresh tokens for a user
- Azure AD Identity Protection detects elevated user risk

In addition, CAE-enabled Microsoft resources can enforce location-based conditional access policies.

## Improve application security and resilience with CAE

The [More secure and resilient apps built on Azure AD Continuous Access Evaluation](https://www.youtube.com/watch?v=Yc9b7L3srrE) video demonstrates building a client app with CAE support.

> [!VIDEO https://www.youtube.com/embed/Yc9b7L3srrE]

Watch the above presentation to learn how applications work when using modern authentication with these steps:

- How applications work when using modern authentication
- App asks Microsoft identity for tokens
- App receives an access token
- App calls API / Authorization with JWT
- Introspection
- Shared signals and events
- Critical event evaluation
- Conditional Access policy evaluation
- Called API Continuous Access Evaluation
- Claims challenge

Continuous Access Evaluation enables an application's authorization to access a resource revoked outside the lifetime of the access token. For example, an application has a token that is valid for 75 more minutes. A user has a high-risk state due to breached credentials. CAE will block the app's access to the resource, requiring the user to reauthenticate before continuing. Thus, CAE achieves its primary goal to improve app security.

As access to a resource can be revoked outside a token's lifetime, Azure AD can issue tokens for a longer lifetime. For apps that support CAE, Azure AD can issue tokens that are valid for up to 28 hours. Although this longer token lifetime doesn't improve the app's resilience, it reduces application costs as the app will need to request tokens much less frequently.

CAE improves an app's resilience to issues that the app could encounter in acquiring an access token from Azure AD. Whenever possible, Azure AD will issue a refresh time as part of a token response that contains an access token. Microsoft Authentication Libraries (MSAL) use this refresh time to proactively refresh the token. The refresh time is some fraction (usually half) of the token's expiration time. As long as MSAL is able to refresh the access token before the token's expiration time, the app is resilient to token refresh problems.

For example, when an app supports CAE, Azure AD issues a token that authorizes the app to call Microsoft Graph that is valid for 24 hours. Azure AD then tells MSAL to proactively refresh the token after 12 hours. If MSAL attempts to refresh the access token fail because the original access token is still valid for 12 more hours, the app is more resilient to problems when it acquires tokens from Azure AD.

## Implementing Continuous Access Evaluation in your app

As described in [How to use Continuous Access Evaluation enabled APIs in your applications](/azure/active-directory/develop/app-resilience-continuous-access-evaluation?tabs=dotnet), both your app and the resource API it's accessing must be CAE-enabled. However, preparing your code to use a CAE enabled resource won't prevent you from using APIs that aren't CAE enabled. Applications that don't use MSAL can add support for [claims challenges, claims requests, and client capabilities](/azure/active-directory/develop/claims-challenge?tabs=dotnet) to use CAE.

## Next steps

- [Continuous access evaluation for workload identities in Azure AD](/azure/active-directory/conditional-access/concept-continuous-access-evaluation-workload) describes the CAE security benefits to an organization.
- [Apply Zero Trust Principles to Authentication Session Management with Continuous Access Evaluation](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/apply-zero-trust-principles-to-authentication-session-management/ba-p/3615343) describes how to secure authentication sessions without affecting user experience and productivity and modernize session management.
- [Increase resilience of authentication and authorization applications you develop](/azure/active-directory/fundamentals/resilience-app-development-overview) introduces a series of articles that provide guidance on increasing resiliency in apps using the Microsoft identity platform and Azure AD. They contain best practices for using tokens and calling resources.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Integrating applications with Azure AD and the Microsoft identity platform](integrate-apps-with-azure-ad-microsoft-identity-platform.md) helps developers to build and integrate apps that IT pros can secure in the enterprise by securely integrate apps with Azure Active Directory (Azure AD) and the Microsoft identity platform.
