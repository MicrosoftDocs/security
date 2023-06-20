---
title: Managing tokens for Zero Trust
description: This article helps you, as a developer, to build security into your applications with ID tokens, access tokens, and security tokens that your app can receive from the Microsoft identity platform.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 03/28/2023
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to secure my applications with ID tokens, access tokens, and security tokens so that I can enhance application security with the principles of least privilege and verify explicitly.
---
# Managing tokens for Zero Trust

In [Zero Trust application development](overview.md), it's important to specifically define your application's intention and its resource access requirements. Your app should request only the access it requires to function as intended. This article helps you, as a developer, to build security into your applications with [ID tokens](/azure/active-directory/develop/id-tokens), [access tokens](/azure/active-directory/develop/access-tokens), and [security tokens](/azure/active-directory/develop/security-tokens) that your app can receive from the [Microsoft identity platform](/azure/active-directory/develop/)*.*

Ensure that your application adheres to the Zero Trust [principle of least privilege](/azure/active-directory/develop/secure-least-privileged-access) and prevents usage in ways that compromise your intention. Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection. Separate your app's sensitive and powerful sections, providing only authorized user access to these areas. Limit users who can use your application and the capabilities that they have in your app.

Build least privilege into how your application manages ID tokens that it receives from the Microsoft identity platform. Information in ID Tokens allows you to verify that a user is who they claim to be. The user or their organization may specify authentication conditions such as providing an MFA, using a managed device, and being in the correct location.

Make it easy for your customers to manage authorizations to your app. Reduce their user provision overhead and the need for manual processes. [Automatic user provisioning](/azure/active-directory/app-provisioning/plan-auto-user-provisioning) allows IT admins to automate user identity creation, maintenance, and removal in target identity stores. Your customers can base automations on changes to users and groups with [app provisioning](/azure/active-directory/app-provisioning/user-provisioning) or [HR driven provisioning](/azure/active-directory/app-provisioning/what-is-hr-driven-provisioning) in Active Directory (Azure AD).

## Using token claims in your apps

Use claims in ID tokens for UX inside your application, as keys in a database, and providing access to the client application. The ID token is the core extension that [OpenID Connect](/azure/active-directory/develop/v2-protocols-oidc) (OIDC) makes to OAuth 2.0. Your app can receive ID tokens alongside or instead of access tokens.

In the standard pattern for security token authorization, an issued ID token allows the application to receive information about the user. Don't use the ID token as an authorization process to access resources. The authorization server issues ID tokens that contain claims with user information that include the following.

- The [audience](/azure/active-directory/develop/access-tokens#payload-claims) (`aud`) claim is your app's client ID. Accept only tokens for your API client ID.
- The `tid` claim is the ID of the tenant that issued the token. The `oid` claim is an immutable value that uniquely identifies the user. Use the unique combination of the `tid` and `oid` claims as a key when you need to associate data with the user. You can use these claim values to connect your data back to the user's ID in Azure AD.
- The `sub` claim is an immutable value that uniquely identities the user. The subject claim is also unique for your application. If you use the `sub` claim to associate data with the user, it's impossible to go from your data and connect it with a user in Azure AD.

Your apps can use the `openid` scope to request an ID token from the Microsoft identity platform. The OIDC standard governs the `openid` scope along with the format and contents of the ID token. OIDC specifies these [scopes](/graph/permissions-reference#openid-connect-oidc-scopes):

- Use the `openid` scope to sign in the user and add a `sub` claim to the ID token. These scopes provide a user ID that is unique to the app and the user and calls the [UserInfo endpoint](/azure/active-directory/develop/userinfo).
- The `email` scope adds an `email` claim containing the user's email address to the ID token.
- The `profile` scope adds claims with basic profile attributes of the user (name, username) to the ID token.
- The `offline_access` scope allows the app to access user data even when the user isn't present.

The [Microsoft Authentication Library](/azure/active-directory/develop/msal-overview) (MSAL) always adds the openid, email, and `profile` scopes to every token request. As a result, MSAL always returns an ID token and an access token on every call to `AcquireTokenSilent` or AcquireTokenInteractive. MSAL always requests the `offline_access` scope. The Microsoft identity platform always returns `offline_access` scope even when the requesting app doesn't specify the `offline_access` scope.

Microsoft uses the OAuth2 standard to issue access tokens. The OAuth2 standard says that you receive a token, but it doesn't specify the token format or what needs to be in the token. When your application needs to access a resource that Azure AD protects, it should use a scope that the resource has defined.

For example, Microsoft Graph defines the User.Read scope that authorizes the application to access the current user's full user profile and the tenant's name. Microsoft Graph defines [permissions](/graph/permissions-reference) across the full range of functionality available in that API.

Upon authorization, the Microsoft identity platform returns an access token to your application. When you call the resource, your app provides this token as part of the authorization header of the HTTP request to the API.

## Managing token lifetimes

Applications can create a session for a user after the authentication successfully completes with Azure AD. User session management drives how frequently a user needs reauthentication. Its role in keeping an explicitly verified user in front of the app with the right privilege and for the right amount of time is crucial. Session lifetime must be based on the `exp` claim in the ID token. The `exp` claim is the time at which the ID token expires and the time after which you can no longer use the token to authenticate the user.

Always respect the [token lifetime](/azure/active-directory/develop/active-directory-configurable-token-lifetimes) as provided in the token response for access tokens or the `exp` claim in the ID token. Conditions that govern token lifetime can include sign-in frequency for an enterprise. Your application can't configure the token lifetime. You can't request a token lifetime.

In general, tokens must be valid and unexpired. The audience claim (aud) must match your client ID. Make sure the token is coming from a trusted issuer. If you have a multitenant API, you may choose to filter so that only specific tenants can call your API. Make sure you enforce the token's lifetime. Check the `nbf` (not before) and the `exp` (expiration) claims to ensure the current time is within those two claims' values.

Don't aim for exceptionally long or short session lifetimes. Let the granted [ID token lifetime](/azure/active-directory/develop/id-tokens#id-token-lifetime) drive this decision. Keeping your app's sessions active beyond token validity violates the rules, policies, and concerns that drove an IT admin to set a token validity duration to prevent unauthorized access. Short sessions degrade user experience and don't necessarily increase the security posture. Popular frameworks like ASP.NET allow you to set session and cookie timeouts from Azure AD's ID token's expiry time. Following the identity provider's token expiry time ensures that your user's sessions are never longer than the policies that the identity provider dictates.

## Caching and refreshing tokens

Remember to appropriately cache tokens. MSAL automatically caches tokens but the tokens have lifetimes. Use tokens through the full length of their lifetimes and appropriately cache them. If you repeatedly ask for the same token, throttling causes your application to become less responsive. If your app abuses the token issuance, the time required for issuing new tokens to your app lengthens.

MSAL libraries manage the details of the OAuth2 protocol including the mechanics of refreshing tokens. If you aren't using MSAL, ensure that your library of choice makes effective use of [refresh tokens](/azure/active-directory/develop/refresh-tokens).

When your client acquires an access token to access a protected resource, it receives a refresh token. Use the refresh token to obtain new access/refresh token pairs after the current access token expires. Use refresh tokens to acquire extra access tokens for other resources. Refresh tokens are bound to a combination of user and client (not to a resource or tenant). You can use a refresh token to acquire access tokens across any combination of resource and tenant where your app has permissions.

## Managing token errors and bugs

Your application should never attempt to validate, decode, inspect, interpret, or examine the contents of an access token. These operations are strictly the responsibility of the resource API. If your app attempts to examine the contents of an access token, it's highly likely that your application breaks when the Microsoft identity platform issues encrypted tokens.

Rarely, a call to retrieve a token can fail due to issues like network, infrastructure, or authentication service failure or outage. [Increase authentication experience resiliency](/azure/active-directory/fundamentals/resilience-app-development-overview) in your application if a token acquisition failure occurs by following these best practices:

- Locally cache and secure tokens with encryption.
- Don't pass security artifacts like tokens around on nonsecure channels.
- Understand and act on exceptions and service responses from the identity provider.

Developers often have questions about looking inside tokens to debug issues such as receiving a 401 error from calling the resource. As more encrypted tokens prevent you from looking inside an access token, you need find alternatives to looking inside access tokens. For debugging, the token response that contains the access token provides the information that you need.

In your code, check for error classes rather than individual error cases. For example, handle user interaction required rather than individual errors where the system hasn't granted permission. Because you may miss those individual cases, it's better to check for a classifier like user interaction rather than dig into individual error codes.

You may need to fall back to `AcquireTokenInteractive` and provide claims challenges that the `AcquireTokenSilent` call requires. Doing so ensures effective management of the interactive request.

## Next steps

- [Customizing tokens](zero-trust-token-customization.md) helps you to understand how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Authenticating users for Zero Trust](user-authentication.md) helps developers to learn best practices for authenticating application users in Zero Trust application development. It describes how to enhance application security with the Zero Trust principles of least privilege and verify explicitly.
- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Configure how users consent to applications](/azure/active-directory/manage-apps/configure-user-consent)
- [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (nonuser applications) on Azure is Managed Identities for Azure resources.
- [Troubleshoot Azure Active Directory access tokens: Validate an access token](/azure/databricks/dev-tools/api/latest/aad/troubleshoot-aad-token#validate-an-access-token)
