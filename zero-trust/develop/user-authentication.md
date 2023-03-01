---
title: Authenticating users for Zero Trust
description: This article helps developers to learn best practices for authenticating application users in Zero Trust application development. It describes how to enhance application security with the Zero Trust principles of least privilege and verify explicitly.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 02/28/2023
ms.custom: template-concept
# Customer intent: As a developer, I want to learn best practices for authenticating my application users in Zero Trust application development so that I can enhance application security with the principles of least privilege and verify explicitly.
---
# Authenticating users for Zero Trust

This article helps you, as a developer, to learn best practices for authenticating your application users in [Zero Trust application development](/azure/active-directory/develop/zero-trust-for-developers). Always enhance your application security with the Zero Trust principles of [least privilege and verify explicitly](/azure/active-directory/develop/secure-least-privileged-access).

## ID tokens in user authentication

When you need a user authenticate to your app, rather than collecting a username and password, your application can request an [identity (ID) token](/azure/active-directory/develop/id-tokens). Authenticating users through the [Microsoft identity platform](/azure/active-directory/develop/v2-overview) avoids security risks that arise when your application retains user credentials. When you request ID tokens, if a bad actor breaches or compromises your application, there are no usernames and corresponding passwords, secrets, and certificates in your app.

The Microsoft identity platform ID token is part of the [Open ID Connect](/azure/active-directory/fundamentals/auth-oidc) (OIDC) standard that specifies ID tokens as [JSON Web Tokens](/azure/active-directory/develop/security-tokens) (JWT). The JWT long string comprises three components:

1. [Header claims](/azure/active-directory/develop/id-tokens#header-claims). The header claims present in ID tokens include `typ` (type claim), `alg` (algorithm for signing the token), and `kid` (thumbprint for the public key to validate the token\'s signature).
1. [Payload claims](/azure/active-directory/develop/id-tokens#payload-claims). The payload or body (the middle part of a JSON web token) contains a series of name attribute pairs. The standard requires that there be a claim with the `iss` (issuer name) that goes to the application that issued the claim (the `aud`, or audience claim).
1. [Signature](/azure/active-directory/develop/access-tokens#validating-the-signature). Azure AD generates the token signature that apps can use to validate that the token is unmodified and you can trust it.

The following example of an ID token shows information about the user and confirms authentication to use the application.

```json
{
  "typ": "JWT",
  "alg": "RS256",
  "kid": "1LTMzakihiRla_8z2BEJVXeWMqo"
}.
{
  "ver": "2.0",
  "iss": "https://login.microsoftonline.com/3338040d-6c67-4c5b-b112-36a304b66dad/v2.0",
  "aud": "6cb04018-a3f5-46a7-b995-940c78f5aef3",
  "exp": 1536361411,
  "iat": 1536274711,
  "nbf": 1536274711,
  "sub": "AAAAAAAAAAAAAAAAAAAAAIkzqFVrSaSaFHy782bbtaQ",
  "name": "Abe Lincoln",
  "preferred_username": "AbeLi@microsoft.com",
  "oid": "00000000-0000-0000-66f3-3332eca7ea81",
  "tid": "3338040d-6c67-4c5b-b112-36a304b66dad",
}.
.[Signature]
```

## ID tokens in access management

To receive your application (client) ID, [register your app](app-registration.md) with the Microsoft identity platform. When you receive a token with an audience claim (`aud`) that matches your app's client ID, the identified user in the token has authenticated to your app. IT admins may allow all users in the tenant to use your app. They may allow a group of which the user is a member to use your app.

If you receive a token whose audience claim is different from your app's client ID, immediately reject the token. The user hasn't authenticated by signing into your app. They signed into another app. Always make sure that the user has permission to use your app.

These claims details are important in user authentication:

- A JSON web token is valid until it expires. The `exp` (expiration) claim tells you when the token expires. If the current time is before the time in the `exp` claim, the token is valid.
- Don't consider the user as authenticated before the time specified in the `nbf` (not before time) claim. The `nbf` and `exp` times of the token define the token's valid lifetime. When the expiration time is imminent, make sure that you get a new ID token.
- The `sub` (subject claim) is a unique identifier for an application user. The same user has a different `sub` claim for other apps. If you want to store data to associate back to a user and prevent an attacker from making that association, use the subject claim. Because it doesn't expose the user's Azure AD identity, it's the most private way to associate data to a user. The `sub` claim is immutable.
- If you want to share information across multiple applications, use the combination of tenant ID (`tid`) and object ID (`oid`) claims that are unique to the user. The combined tenant ID and object ID are immutable.
- No matter what happens to an individual\'s identity, the `sub`, `oid`, and `tid` claims remain immutable. Anything about the user can change and you can still key your data off identifying the user based on the subject or the combined `tid` and `oid` claims.

## Authentication with OIDC

To demonstrate user authentication, let's look at applications that use OIDC to authenticate a user. The same principles apply to apps that use SAML or WS-Federation.

An app authenticates the user when the application requests an ID token from the Microsoft identity platform. Workloads (applications that don't have users present but rather run as services, background processes, daemons) skip this step.

You should always silently ask for this token first. To silently acquire a token in [Microsoft Authentication Libraries](/azure/active-directory/develop/msal-overview) (MSAL), your app can start with the `AcquireTokenSilent` method. If your app can authenticate without disturbing the user, it receives the requested ID token.

If the Microsoft identity platform can't complete the request without interacting with the user, then your app needs to fall back to the MSAL `AcquireTokenInteractive` method. To interactively acquire a token, perform the request by opening a web surface to an address under the `https://login.microsoftonline.com` domain.

From this web surface, the user has a private conversation with the Microsoft identity platform. Your app has no view into this conversation, nor does it have any control of the conversation. The Microsoft identity platform can ask for a user ID and password, multifactor authentication (MFA), passwordless authentication, or other authentication interaction that the IT admin or user has configured.

Your application will receive an ID token after the user has performed required authentication steps. When your app receives the token, you can be certain that the Microsoft identity platform has authenticated the user. If your app doesn't receive an ID token, the Microsoft identity platform hasn't authenticated the user. Don't allow unauthenticated users to continue into secured areas of your app.

It's best practice for applications to create a session for a user after it receives an ID token from Azure Active Directory (Azure AD). In the ID token that an app receives, an expiration (`exp`) claim with a Unix timestamp. This timestamp specifies the *on or after* expiration time for which the app mustn't accept the JWT for processing. Use this token expiration time to drive the lifetime of your user sessions. The `exp` claim plays a crucial role in keeping an explicitly verified user in front of the app with the right privilege and for the right amount of time.

## Single Sign On support

[Single sign-on](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) authentication allows users to sign in with one set of credentials to multiple independent software systems. SSO allows application developers to not require a user to sign in to every application separately and repeatedly. At the core of SSO, developers ensure that all applications on the user's device share the web surface that authenticates the user. Artifacts on the web surface (such as session state and cookies) after successful authentication drive SSO.

As illustrated in the following diagram, the simplest use case of a shared web surface is an app that's running in a web browser (such as Microsoft Edge, Google Chrome, Firefox, Safari). Browser tabs share the SSO state.

:::image type="complex" source="../media/develop/user-authentication/diagram-web-browser-simplest-case-inline.png" alt-text="Diagram illustrates the shared web surface scenario where an app is running in a browser." lightbox="../media/develop/user-authentication/diagram-web-browser-simplest-case-expanded.png":::
   Diagram title: Web browser – simplest case. Appearing at the top center of the diagram is a cloud shape containing an Azure AD icon. Below the cloud shape is a box. Connecting the cloud shape and the box is a line with an arrow on each end. The box label is "Keep me signed in, saves SSO state cookies across invocations." Inside the box, on the left side, is an icon that looks like a cookie. Below the cookie, the caption is "Private conversation with the user." Below the caption is an icon that represents the user. To the left of these three components, inside the box, is another box. The internal box label is "Tabs." Below the label are four square boxes that represent browser windows in tabs.
:::image-end:::

The Microsoft identity platform manages the SSO state in any specific browser unless the user has different browsers open on the same device. On Windows 10 and newer, the Microsoft identity platform natively supports browser SSO in Internet Explorer and Microsoft Edge. When the user has signed into Windows, accommodations in Google Chrome (via the Windows 10 accounts extension) and in Mozilla Firefox v91+ (via a browser setting) allow each browser to share the SSO state.

As shown in the following diagram, the native application use case is more complicated.

:::image type="complex" source="../media/develop/user-authentication/diagram-native-app-embedded-browser-no-sso-inline.png" alt-text="Diagram illustrates the complicated native application use case of embedded browsers without SSO." lightbox="../media/develop/user-authentication/diagram-native-app-embedded-browser-no-sso-expanded.png":::
   Diagram title: Native applications – embedded browsers – no SSO. Appearing at the top center of the diagram is a cloud shape containing an Azure AD icon. At the bottom of the diagram are four boxes spread horizontally. At the bottom right corner of each box is an icon that represents a user. Inside each of the boxes is a representation of browser windows, including a cookie icon and a globe icon. Connecting each of the four boxes to the cloud shape is a line with an arrow on each end.
:::image-end:::

## Auth broker approach

A common pattern is for each native app to have its own embedded WebView that prevents it from participating in SSO. To address this scenario, Azure AD uses an [authentication broker](/windows/uwp/security/web-authentication-broker) (auth broker) approach for native applications as illustrated in the following diagram.

:::image type="complex" source="../media/develop/user-authentication/diagram-auth-broker-approach-inline.png" alt-text="Diagram illustrates the use of authentication brokers for native applications." lightbox="../media/develop/user-authentication/diagram-auth-broker-approach-expanded.png":::
   Diagram title: Auth broker approach. Appearing at the top center of the diagram is a cloud shape containing an Azure AD icon. Below the cloud shape is a rectangle shape with the label, Auth Broker. The rectangle shape contains a cookie icon and a globe icon. Connecting the cloud shape and the rectangle shape is a line with an arrow on each end. At the bottom of the diagram are four boxes spread horizontally. At the bottom right corner of each box is an icon that represents a user. Icons in each box represent browser windows. Connecting each of the four boxes to the rectangle shape is a line with an arrow on each end.
:::image-end:::

With an auth broker in place, applications send authentication requests to the broker instead of directly to the Microsoft identity platform. In this way, the broker becomes the shared surface for all authentication on the device.

In addition to providing a shared surface, the auth broker provides other benefits. When adopting Zero Trust, enterprises may want to have applications run only from enterprise managed devices. Examples of enterprise device management include full Mobile Device Management (MDM) and scenarios where users bring their own devices that participate in Mobile Application Management (MAM).

By design, underlying operating systems (OS) isolate browsers. Developers need a closer connection with the OS to have full access to device details. In Windows, the auth broker is the Windows [Web Account Manager](/windows/uwp/security/web-account-manager) (WAM). On other devices, the auth broker is either the Microsoft Authenticator app (for devices running iOS or Android) or the Company Portal App (for devices running Android). Applications access the auth broker with MSAL. In Windows, an app can access the WAM without MSAL. However, MSAL is the easiest way for apps to access the auth broker (especially apps that aren't Universal Windows Platform apps).

Auth brokers work in combination with Azure AD to utilize [Primary Refresh Tokens](/azure/active-directory/devices/concept-primary-refresh-token) (PRT) that reduce the need for users to authenticate multiple times. PRTs can determine whether the user is on a managed device. Azure AD requires auth brokers as it introduces [Proof of Possession tokens](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Proof-Of-Possession-(PoP)-tokens), a more secure option over the bearer tokens that are prevalent today.

## Next steps

- [Troubleshoot Azure Active Directory access tokens: Validate an access token](/azure/databricks/dev-tools/api/latest/aad/troubleshoot-aad-token#validate-an-access-token) describes how, when you have an Azure AD access token, you verify that certain fields match the record.
- The [Increase resilience of authentication and authorization applications you develop](/azure/active-directory/fundamentals/resilience-app-development-overview) article series addresses apps that use the Microsoft identity platform and Azure AD. They include guidance for client and service applications that work on behalf of a signed in user and daemon applications that work on their own behalf. They contain best practices for using tokens and calling resources.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how you can customize tokens.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles.
- [Building apps that secure identity through permissions and consent](identity.md) provides an overview of permissions and access best practices.
