---
title: Authorization best practices
description: As a developer, implement the best authorization, permission, and consent models for your applications.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.service: zero-trust
ms.date: 02/24/2025
ms.collection:
  - zerotrust-dev
ms.custom:
  - template-concept
  - sfi-image-nochange
# Customer intent: As a developer, I want to implement the best authorization, permission, and consent models for my applications.
---
# Authorization best practices

As you learn to [develop using Zero Trust principles](overview.md), this article continues from [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md), [Develop delegated permissions strategy](developer-strategy-delegated-permission.md), and [Develop application permissions strategy](developer-strategy-application-permissions.md). It helps you, as a developer, to implement the best authorization, permission, and consent models for your applications.

You can [implement authorization](/entra/identity-platform/authorization-basics#implementing-authorization) logic within applications or solutions that require access control. When authorization approaches rely on information about an authenticated entity, an application can evaluate information that is exchanged during authentication (for example, information provided within a [security token](/entra/identity-platform/security-tokens)). When a security token doesn't contain information, an application can make calls to external resources.

You don't have to embed authorization logic entirely within your application. You can use dedicated authorization services to centralize authorization implementation and management.

## Best practices for permissions

The most widely adopted applications in Microsoft Entra ID follow consent and authorization best practices. Review [Best practices for working with Microsoft Graph](/graph/best-practices-concept) and [Microsoft Graph permissions reference](/graph/permissions-reference) to learn how to be thoughtful with your permission requests.

- **Apply [least privilege](/entra/identity-platform/secure-least-privileged-access).** Only request necessary permissions. Use incremental consent to request granular permissions just in time. Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.

- **Use the correct [permission type](/entra/identity-platform/permissions-consent-overview) based on scenarios**. Avoid using both application and delegated permissions in the same app. If you build an interactive application where a signed-in user is present, use *delegated permissions*. If, however, your application runs [without a signed-in user](identity-non-user-applications.md), such as a background service or daemon, use *application permissions*.

- **Provide [terms of service and privacy statements](/entra/identity-platform/howto-add-terms-of-service-privacy-statement).** The user consent experience surfaces your terms of service and privacy statement to users to help them know that they can trust your app. They're especially critical for user-facing multitenant apps.

## When to request permission

Some permissions require an administrator to grant consent within a tenant. They can use the admin consent endpoint to grant permissions to an entire tenant. To request permissions or scopes, you can follow these models.

- **Implement dynamic user consent at sign-in or first access token request.** Dynamic user consent doesn't require anything in your app registration. You can define the scopes that you need under certain conditions (for example, when you sign in a user for the first time). After you request that permission and receive consent, you won't need to request permission. However, if you don't receive dynamic user consent at sign-in or first access, then it goes through the permission experience.

- **Request incremental user consent as needed.** With incremental consent combined with dynamic user consent, you don't have to request all of the permissions at any one time. You can request a few permissions. As the user moves to different functionality in your application, you request more consent. This approach can increase the user's comfort level as they incrementally grant permissions to your application. For example, if your application requests OneDrive access, it might arouse suspicion if you also request Calendar access. Instead, later ask the user to add Calendar reminders against their OneDrive.

- **Use the `/.default` scope.** The `/.default` scope effectively mimics the old default experience that looked at what you put in the application registration, figured out what consents you needed, and then asked for all of the consents not yet granted. It doesn't require you to include the permissions that you need in your code because they're in your app registration.

## Become a Verified Publisher

Microsoft customers sometimes describe difficulty in deciding when to allow an application to access the Microsoft identity platform by signing in a user or calling an API. While adopting [Zero Trust principles](../zero-trust-overview.md), they want:

- Increased visibility and control.
- More proactive and easier reactive decisions.
- Systems that keep data safe and reduce the decision burden.
- Accelerated app adoption for trustworthy developers.
- Restricted consent to apps with low-risk permissions that are publisher verified.

While access to data in APIs like Microsoft Graph allows you to build rich applications, your organization or your customer evaluates the permissions that your app requests along with your app's trustworthiness.

Becoming a [Microsoft Verified Publisher](/entra/identity-platform/publisher-verification-overview) helps you to give your customers an easier experience in accepting your application requests. When an application comes from a verified publisher, users, IT Pros, and customers know that it comes from someone with whom Microsoft has a business relationship. A blue checkmark appears next to the publisher's name (component #5 in the following **Permissions requested** consent prompt example. Reference the component table at [Microsoft Entra application consent experience](/entra/identity-platform/application-consent-experience#building-blocks-of-the-consent-prompt)). The user can select the verified publisher from the consent prompt to view more information.

:::image type="complex" source="../media/develop/developer-strategy-authorization-best-practices/screenshot-application-permissions-requested-consent-prompt-inline.png" alt-text="Screenshot of Permissions requested dialog shows component building blocks as described in linked Microsoft Entra application consent experience article." lightbox="../media/develop/developer-strategy-authorization-best-practices/screenshot-application-permissions-requested-consent-prompt-expanded.png":::
   "Screenshot of the consent experience Permissions requested dialog."
:::image-end:::

When you're a verified publisher, users and IT pros gain trust in your application because you're a verified entity. Publisher verification provides improved branding for your application, and increased transparency, reduced risk, and smoother enterprise adoption for your
customers.

## Next steps

- [Develop delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop with Zero Trust principles.
- [Develop application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Security best practices for application properties](/entra/identity-platform/security-best-practices-for-app-registration) describes redirect URI, access tokens, certificates and secrets, application ID URI, and application ownership.
- [Customize tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens. It explains how to customize tokens to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [Configure group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles. These methods help to improve flexibility and control while increasing application Zero Trust security with least privilege.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
