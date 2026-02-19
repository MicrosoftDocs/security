---
title: Call an API from another API
description: Ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
author: janicericketts
ms.author: jricketts
ms.subservice: zero-trust
ms.topic: concept-article
ms.service: security
ms.date: 04/18/2025
ms.collection:
  - zerotrust-dev
ms.custom:
  - template-concept
  - sfi-image-nochange
# Customer intent: As a developer, I want to ensure Zero Trust when I have one API that needs to call another API so that I can securely develop my application when it is working on behalf of a user.
---
# Call an API from another API

How do you, as a developer, [ensure Zero Trust](overview.md) when you have one API that needs to call another API? In this article, you learn how to securely develop your application when it's working on behalf of a user.

When a user drives an app's UI, the app might use a delegated permission so that the API knows which user on whose behalf the app is working. It inspects the subject (`sub`) claim or object ID (`oid`) and tenant ID (`tid`) claims in the access token that the app provides when calling the API. The API doesn't rely on the untrusted app, which is just a call coming from somewhere on the network. Instead, it validates the token to ensure that the API only works on behalf of the app user that Microsoft Entra ID verified.

When one API (we refer to it as the *Original API*) calls another, it's vital that the API that we're calling (we refer to it as the *Downstream API*) follows the validation process. The Downstream API can't rely on an untrusted network source. It must get the user identity from a properly validated access token.

If the Downstream API doesn't follow the proper validation process, the Downstream API must rely on the Original API to provide the identity of the user in another way. The Downstream API might incorrectly use an application permission to perform the operation. Then the Original API then becomes the sole authority over which users can achieve which results against the Downstream API. The Original API can intentionally (or unintentionally) allow a user to accomplish a task that the user can't otherwise accomplish. For example, one user can change the details of another user or read and update documents that the user doesn't have permission to access. Improper validation can cause serious security issues.

For better security, the Original API acquires a [delegated permission](developer-strategy-delegated-permission.md) access token to provide to the Downstream API when the Original API makes the call. Let's walk through how this works.

1. **Client App acquires access token to call Original API.** The Client Application acquires a delegated permission access token to the Original API. The delegated permission access token allows it to work on behalf of the user to call the Original API that requires authorization.
1. **Client App gives access token to Original API.** The Client App gives the access token to the Original API. The Original API fully validates and inspects the access token to determine the identity of the Client App's user.
1. **Original API performs token validation and enforcement.** After the Client App gives the access token to the Original API, the Original API performs token validation and enforcement. If all is good, the API proceeds and services the request for the Client App.
1. **Original API can't use access token to call Downstream API.** The Original API wants to call a Downstream API. However, the Original API can't use the access token to call the Downstream API.
1. **Original API goes back to Microsoft Entra ID.** The Original API needs to go back to Microsoft Entra ID. It needs an access token to call the Downstream API on behalf of the user. The Original API provides the token that the Original API received from the Client App and the Original API's client credentials.
1. **Microsoft Entra ID performs checks.** Microsoft Entra ID checks for things like consent or conditional access enforcement. You might have to go back to your calling client and provide a reason for not being able to get the token. You would typically use a [claims challenge](/entra/identity-platform/claims-challenge) process to go back to the calling application with information regarding consent not being received (such as being related to conditional access policies). If everything is okay, Microsoft Entra ID issues an access token to the Original API to call the Downstream API on behalf of the user.
1. **Original API has user context with On-Behalf-Of flow.** The [On-Behalf-Of flow](/entra/identity-platform/v2-oauth2-on-behalf-of-flow) (OBO) process allows an API to continue to have the user context as it calls Downstream API.
1. **Original API calls Downstream API.** Call the Downstream API. The token that the Downstream API receives has the proper audience (aud) claim that indicates the Downstream API. The token includes the scopes for granted consent and the original app user identity. The Downstream API can properly implement effective permissions to ensure that the identified user has permission to accomplish the requested task. You want to use the on behalf of flow to acquire tokens for an API to call another API to make sure that user context passes to all Downstream APIs.

## Best option: Original API performs On-Behalf-Of flow

The best option is for the Original API to perform On-Behalf-Of flow (OBO). If the Downstream API receives the correct token, it can correctly respond. When an API is acting on behalf of a user and needs to call another API, the API must use OBO to acquire a delegated permission access token to call the Downstream API on behalf of the user. APIs should never use application permissions to call Downstream APIs when the API is acting on behalf of a user.

## Next steps

- [Microsoft identity platform authentication flows & app scenarios](/entra/identity-platform/authentication-flows-app-scenarios) describes authentication flows and the application scenarios in which they\'re used.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Example of API protected by Microsoft identity consent framework](protected-api-example.md) helps you to design least privilege application permissions strategies for the best user experience.
- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- The [Secure custom APIs with Microsoft Identity](/training/modules/identity-secure-custom-api/) Learn module explains how to secure a web API with Microsoft identity and how to call it from another application.
- [Security best practices for application properties](/entra/identity-platform/security-best-practices-for-app-registration) describes redirect URI, access tokens, certificates and secrets, application ID URI, and application ownership.
- [Microsoft identity platform authentication libraries](/entra/identity-platform/reference-v2-libraries) describes Microsoft Authentication Library support for various application types.
