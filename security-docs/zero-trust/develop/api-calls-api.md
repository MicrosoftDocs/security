---
title: Call an API from another API
description: Ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 05/24/2024
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to ensure Zero Trust when I have one API that needs to call another API so that I can securely develop my application when it is working on behalf of a user.
---
# Call an API from another API

How do you, as a developer, [ensure Zero Trust](overview.md) when you have one API that needs to call another API? In this article, you learn how to securely develop your application when it's working on behalf of a user.

When a user drives an app's UI, the app might use a delegated permission so that the API knows which user on whose behalf the app is working. It would inspect the subject (sub) claim or object ID (oid) and tenant ID (tid) claims in the access token that the app provides when calling the API. The API wouldn't rely on the untrusted app, which is just a call coming from somewhere on the network. Instead, it would validate the token to ensure that the API only works on behalf of the app user that Microsoft Entra ID verified.

When one API (we refer to it as the *Original API*) calls another, it's vital that the API that we're calling (we refer to it as the *Downstream API*) follows the above-described validation process. The Downstream API can't rely on an untrusted network source. It must get the user identity from a properly validated access token.

If the Downstream API doesn't follow the proper validation process, the Downstream API must rely on the Original API to provide the identity of the user in another way. The Downstream API might incorrectly use an application permission to perform the operation. Then the Original API would become the sole authority over which users could achieve which results against the Downstream API. The Original API could intentionally (or unintentionally) allow a user to accomplish a task that the user couldn't otherwise accomplish. For example, one user could change the details of another user or read and update documents that the user doesn't have permission to access. Improper validation can cause serious security issues.

For better security, the Original API acquires a [delegated permission](developer-strategy-delegated-permission.md) access token to provide to the Downstream API when the Original API makes the call. Let's walk through how this works.

## Client App acquires access token to call Original API

The following diagram shows the Client App and the Original API.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-01-inline.png" alt-text="Diagram shows Client App with ID and access tokens and the Original API that requires authorization." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-01-expanded.png":::
    Diagram title: The Client App acquired an access token to call the Original API. Diagram subtitle: The Client Application has an access 'A' token that allows it to work on behalf of user identified in token to call the Original API.
:::image-end:::

The Client Application acquired a delegated permission access token (indicated by the pentagon shape with the "A" label) to the Original API. The delegated permission access token allows it to work on behalf of the user to call the Original API that requires authorization.

## Client App gives access token to Original API

The following animation shows the Client App giving the access token to the Original API. The Original API fully validates and inspects the access token to determine the identity of the Client App's user.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-01-to-02-inline.gif" alt-text="Animated diagram shows Client App giving an access token to the Original API that requires authorization." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-01-to-02-expanded.gif":::
    The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: The Client App acquired an access token to call the Original API. First diagram subtitle: The Client Application has an access 'A' token that allows it to work on behalf of user identified in token to call the Original API. Second diagram title: The Client App gives the access token to the Original API.
:::image-end:::

## Original API performs token validation and enforcement

The next animation shows that, after the Client App gives the access token to the Original API, the Original API performs token validation and enforcement. If all is good, the API proceeds and services the request for the Client App.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-02-to-03-inline.gif" alt-text="Animated diagram shows Client App with ID token on the left giving the access token to the Original API on the right." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-02-to-03-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: The Client App gives the access token to the Original API. Second diagram title: The Original API performs token validation and enforcement. If all good, the API proceeds and services the request.
:::image-end:::

## Original API can't use access token to call Downstream API

The following animation shows that the Original API now wants to call a Downstream API. However, the Original API can't use the access token to call the Downstream API.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-04-to-05-inline.gif" alt-text="Animated diagram shows Client App giving access token to Original API. Authorization Required prevents Original API from giving token to Downstream API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-04-to-05-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: The Original API wants to call a Downstream API. Second diagram title: The Original API can't use the token to call the Downstream API.
:::image-end:::

## Original API goes back to Microsoft Entra ID

In the following animation, the Original API needs to go back to Microsoft Entra ID. It needs an access token to call the Downstream API on behalf of the user.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-05-to-06-inline.gif" alt-text="Animated diagram shows Client App giving access token to Original API that needs validation from Microsoft Entra ID to call Downstream API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-05-to-06-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: The Original API can't use the token to call the Downstream API. Second diagram title: Original API goes back to Microsoft Entra ID. Second diagram subtitle: Needs an access token to call the Downstream API on behalf of the user.
:::image-end:::

The next animation shows the Original API providing the token that the Original API received from the Client App and the Original API's client credentials.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-06-to-07-inline.gif" alt-text="Animated diagram shows Client App giving access token to Original API that receives validation from Microsoft Entra ID to call Downstream API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-06-to-07-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: Original API goes back to Microsoft Entra ID. First diagram subtitle: Needs an access token to call the Downstream API on behalf of the user. Second diagram title: Original API goes back to Microsoft Entra ID. Second diagram subtitle: Provides the token from the Client App and the credentials for the Original API.
:::image-end:::

Microsoft Entra ID checks for things like consent or conditional access enforcement. You might have to go back to your calling client and provide a reason for not being able to get the token. You would typically use a [claims challenge](/entra/identity-platform/claims-challenge) process to go back to the calling application with information regarding consent not being received (such as being related to conditional access policies).

## Microsoft Entra ID performs checks

In the following animation, Microsoft Entra ID performs its checks. If everything is okay, Microsoft Entra ID issues an access token to the Original API to call the Downstream API on behalf of the user.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-07-to-08-inline.gif" alt-text="Animated diagram shows Original API giving access token to Downstream API after validating with Microsoft Entra ID." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-07-to-08-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: Original API goes back to Microsoft Entra ID. First diagram subtitle: Provides the token from the Client App and the credentials for the Original API. Second diagram title: Microsoft Entra ID checks conditional access, consent, etc. Second diagram subtitle: The Original API receives its own access token to call the Downstream API on behalf of the user who signed into the Client App.
:::image-end:::

## Original API has user context with On-Behalf-Of flow

The following animation illustrates the [On-Behalf-Of flow](/entra/identity-platform/v2-oauth2-on-behalf-of-flow) (OBO) process that allows an API to continue to have the user context as it calls Downstream API.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-09-to-10-inline.gif" alt-text="Animated diagram shows Original API giving access token to Downstream API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-09-to-10-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: On-Behalf-Of flow process allows the Original API to continue to have user context as it calls the Downstream API. Second diagram title: On-Behalf-Of flow process allows the Original API to continue to have user context as it calls the Downstream API.
:::image-end:::

## Original API calls Downstream API

In the next animation, we call the Downstream API. The token that the Downstream API receives has the proper audience (aud) claim that indicates the Downstream API.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-10-to-11-inline.gif" alt-text="Animated diagram shows Downstream API validating access token from Original API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-10-to-11-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: On-Behalf-Of flow process allows the Original API to continue to have user context as it calls the Downstream API. Second diagram title: The Downstream API is called. Second diagram subtitle: The token that the Downstream API receives has proper claims to identify the user of the Client App.
:::image-end:::

The token includes the scopes for granted consent and the original app user identity. The Downstream API can properly implement effective permissions to ensure that the identified user has permission to accomplish the requested task. You want to use the on behalf of flow to acquire tokens for an API to call another API to make sure that user context passes to all Downstream APIs.

## Best option: Original API performs On-Behalf-Of flow

This last animation shows that the best option is for the Original API to perform On-Behalf-Of flow (OBO). If the Downstream API receives the correct token, it can correctly respond.

:::image type="complex" source="../media/develop/api-calls-api/diagram-API-calls-API-slide-11-to-12-inline.gif" alt-text="Animated diagram shows Downstream API receiving access token from Original API." lightbox="../media/develop/api-calls-api/diagram-API-calls-API-slide-11-to-12-expanded.gif":::
   The animated diagram shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: The Downstream API is called. First diagram subtitle: The token that the Downstream API receives has proper claims to identify the user of the Client App. Second diagram title: The best option is for the Original API to perform "on behalf of flow." If the Downstream API receives the correct token, it can correctly respond.
:::image-end:::

When an API is acting on behalf of a user and needs to call another API, the API must use OBO to acquire a delegated permission access token to call the Downstream API on behalf of the user. APIs should never use application permissions to call Downstream APIs when the API is acting on behalf of a user.

## Next steps

- [Microsoft identity platform authentication flows & app scenarios](/entra/identity-platform/authentication-flows-app-scenarios) describes authentication flows and the application scenarios in which they\'re used.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Example of API protected by Microsoft identity consent framework](protected-api-example.md) helps you to design least privilege application permissions strategies for the best user experience.
- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- The [Secure custom APIs with Microsoft Identity](/training/modules/identity-secure-custom-api/) Learn module explains how to secure a web API with Microsoft identity and how to call it from another application.
- [Security best practices for application properties](/entra/identity-platform/security-best-practices-for-app-registration) describes redirect URI, access tokens, certificates and secrets, application ID URI, and application ownership.
- [Microsoft identity platform authentication libraries](/entra/identity-platform/reference-v2-libraries) describes Microsoft Authentication Library support for various application types.
