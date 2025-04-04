---
title: Secure applications with Continuous Access Evaluation
description: Learn how to improve application security with Continuous Access Evaluation and acquire access tokens from Microsoft Entra ID.
ms.date: 02/24/2025
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to improve application security with Continuous Access Evaluation. I want to learn how to ensure Zero Trust support in my apps that receive authorization to access resources when they acquire access tokens from Microsoft Entra ID.
---
# Secure applications with Continuous Access Evaluation

This article helps you, as a developer, to improve application security with Continuous Access Evaluation. You learn how to [ensure Zero Trust support](overview.md) in your apps that receive [authorization to access resources](acquire-application-authorization-to-access-resources.md) when they acquire access tokens from Microsoft Entra ID.

When Microsoft Entra ID issues these access tokens, it fully evaluates the [conditions for that authorization](/entra/identity/conditional-access/overview). Microsoft Entra ID performs standard authorization actions, such as [ensuring consent](identity.md), every time it issues tokens for initial token requests and when it refreshes tokens.

Microsoft Entra ID primarily uses JSON Web Tokens (JWT) for access tokens. A resource API can decode, validate, and interpret the JWT without needing to call back to Microsoft Entra ID on every call to the resource API. The [JWT standard](https://www.rfc-editor.org/rfc/rfc7519) defines an exp claim that identifies the *on-or-after* expiration time that you must not accept the JWT token for processing. By default, Microsoft Entra tokens expire 60 to 90 minutes after issue. Ensure that your applications cache and use access tokens for the period during which Microsoft Entra ID doesn't evaluate authorization conditions.

## Evaluate conditions outside of issuing the token

Lags can occur between user condition changes and policy change enforcement when Microsoft Entra ID issues tokens. A reduced token lifetime approach can degrade user experiences and reliability without eliminating risks.

One solution is to evaluate conditions on every call to a protected resource. The most common way to implement this enforcement is token introspection. Token introspection doesn't use a JWT format for the token. Instead, token introspection uses an opaque string that the resource API can't interpret. The resource API sends the token to the identity provider on each call. The identity provider then checks for any conditions and returns data that the resource API can use to complete the operation. This process can be expensive as it adds another round trip web request to every API call.

To remedy this expense with [Continuous Access Evaluation](/entra/identity/conditional-access/concept-continuous-access-evaluation) (CAE), a resource API can listen for events that Microsoft Entra ID pushes about the tokens that Microsoft Entra ID issues for the resource API. For example, when your application calls the Microsoft Graph API, Microsoft Graph can check if it received events from Microsoft Entra ID about the token. If the conditions of the original authentication are different and the user needs to reauthenticate, Microsoft Graph returns an error to the calling app.

Microsoft Entra ID sends an event to CAE-enabled Microsoft resources when any of these events occur:

- Disabled or deleted user account
- Changed or reset user password
- Enabled user multifactor authentication
- Administrator explicitly revokes all refresh tokens for a user
- Microsoft Entra ID Protection detects elevated user risk

In addition, CAE-enabled Microsoft resources can enforce location-based conditional access policies.

## Improve application security and resilience with CAE

The following [More secure and resilient apps built on Microsoft Entra Continuous Access Evaluation](https://www.youtube.com/watch?v=Yc9b7L3srrE) video demonstrates building a client app with CAE support.

> [!VIDEO https://www.youtube.com/embed/Yc9b7L3srrE]

The video presentation describes how applications work with modern authentication and these steps:

1. App asks Microsoft identity for tokens
1. App receives an access token
1. App calls API / Authorization with JWT
1. Introspection
1. Shared signals and events
1. Critical event evaluation
1. Conditional Access policy evaluation
1. Called API Continuous Access Evaluation
1. Claims challenge

Continuous Access Evaluation enables an application's authorization to access a resource revoked outside the lifetime of the access token. For example, an application has a token that is valid for 75 more minutes. A user has a high-risk state due to breached credentials. CAE blocks the app's access to the resource, requiring the user to reauthenticate before continuing. Thus, CAE achieves its primary goal to improve app security.

As access to a resource can be revoked outside a token's lifetime, Microsoft Entra ID can issue tokens for a longer lifetime. For apps that support CAE, Microsoft Entra ID can issue tokens that are valid for up to 28 hours. Although this longer token lifetime doesn't improve the app's resilience, it reduces application costs as the app needs to request tokens much less frequently.

CAE improves an app's resilience to issues that the app could encounter in acquiring an access token from Microsoft Entra ID. Whenever possible, Microsoft Entra ID issues a refresh time as part of a token response that contains an access token. Microsoft Authentication Libraries (MSAL) use this refresh time to proactively refresh the token. The refresh time is some fraction (usually half) of the token's expiration time. As long as MSAL can refresh the access token before the token's expiration time, the app is resilient to token refresh problems.

For example, when an app supports CAE, Microsoft Entra ID issues a token that authorizes the app to call Microsoft Graph that is valid for 24 hours. Microsoft Entra ID then tells MSAL to proactively refresh the token after 12 hours. If MSAL attempts to refresh the access token fail because the original access token is still valid for 12 more hours, the app is more resilient to problems when it acquires tokens from Microsoft Entra ID.

## Implement Continuous Access Evaluation in your app

As described in [How to use Continuous Access Evaluation enabled APIs in your applications](/entra/identity-platform/app-resilience-continuous-access-evaluation?tabs=dotnet), both your app and the resource API it's accessing must be CAE-enabled. However, preparing your code to use a CAE-enabled resource doesn't prevent you from using APIs that aren't CAE-enabled. Applications that don't use MSAL can add support for [claims challenges, claims requests, and client capabilities](/entra/identity-platform/claims-challenge?tabs=dotnet) to use CAE.

## Next steps

- [Continuous access evaluation for workload identities in Microsoft Entra ID](/entra/identity/conditional-access/concept-continuous-access-evaluation-workload) describes the CAE security benefits to an organization.
- [Apply Zero Trust Principles to Authentication Session Management with Continuous Access Evaluation](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/apply-zero-trust-principles-to-authentication-session-management/ba-p/3615343) describes how to secure authentication sessions without affecting user experience and productivity and modernize session management.
- [Increase resilience of authentication and authorization applications you develop](/entra/architecture/resilience-app-development-overview) introduces a series of articles that provide guidance on increasing resiliency in apps using the Microsoft identity platform and Microsoft Entra ID. They contain best practices for using tokens and calling resources.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Integrate applications with Microsoft Entra ID and the Microsoft identity platform](integrate-apps-microsoft-identity-platform.md) helps developers to build and integrate apps that IT pros can secure in the enterprise.
