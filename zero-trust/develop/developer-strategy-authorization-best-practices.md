---
title: Authorization best practices
description: As a developer, implement the best authorization, permission, and consent models for your applications.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 08/31/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to implement the best authorization, permission, and consent models for my applications.
---
# Authorization best practices

As you learn to [develop using Zero Trust principles](overview.md), this article continues from [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md), [Developing delegated permissions strategy](developer-strategy-delegated-permission.md), and [Developing application permissions strategy](developer-strategy-application-permissions.md) to help you, as a developer, to implement the best authorization, permission, and consent models for your applications.

You can [implement authorization](/azure/active-directory/develop/authorization-basics#implementing-authorization) logic within applications or solutions that require access control. When authorization approaches rely on information about an authenticated entity, an application can evaluate information that is exchanged during authentication (e.g., information provided within a [security token](/azure/active-directory/develop/security-tokens)). When a security token does not contain information, an application can make calls to external resources.

You don't have to embed authorization logic entirely within your application. You can use dedicated authorization services to centralize authorization implementation and management.

## Best practices for permissions

The most widely adopted applications in Azure Active Directory (Azure AD) follow consent and authorization best practices. Review [Best practices for working with Microsoft Graph](/graph/best-practices-concept) and [Microsoft Graph permissions reference](/graph/permissions-reference) to learn how to be thoughtful with your permission requests.

- **Apply [least privilege](/azure/active-directory/develop/secure-least-privileged-access).** Only request absolutely necessary permissions. Use incremental consent to request granular permissions just in time. Limit user access with Just-In-Time and Just-Enough-Access (JIT/JEA), risk-based adaptive policies, and data protection.

- **Use the correct [permission type](/azure/active-directory/develop/permissions-consent-overview) based on scenarios**. Avoid using both application and delegated permissions in the same app. If you're building an interactive application where a signed-in user is present, your application should use *delegated permissions*. If, however, your application runs [without a signed-in user](identity-non-user-applications.md), such as a background service or daemon, your application should use *application permissions*.

- **Provide [terms of service and privacy statements](/azure/active-directory/develop/howto-add-terms-of-service-privacy-statement).** The user consent experience surfaces your terms of service and privacy statement to users to help them know that they can trust your app. They are especially critical for user-facing multi-tenant apps.

## When to request permission

Some permissions require an administrator to grant consent within a tenant. They can use the admin consent endpoint to grant permissions to an entire tenant. There are three models that you can follow to request permissions or scopes.

- **Implement dynamic user consent at login or first access token request.** Dynamic user consent doesn't require anything in your app registration. You can simply define the scopes that you need under certain conditions (e.g., when you sign in a user for the first time). After you request that permission and receive consent, you won't need to request permission but, if you haven't received dynamic user consent at login or first access, then it goes through the permission experience.

- **Request incremental user consent as needed.** With incremental consent combined with dynamic user consent, you don't have to request all of the permissions at any one time. You can request a few permissions and then, as the user moves to different functionality in your application, you request additional consent. That can increase the user's comfort level as they incrementally grant permissions to your application. For example, if your application helps the user with their OneDrive and requests permission to access OneDrive files, it may arouse the user's suspicion if you're also requesting access to their Calendar. Instead, you can later ask the user if they want your app to add Calendar reminders against their OneDrive.

- **Use the `/.default` scope.** The `/.default` scope effectively mimics the old default experience that looked at what you put in the application registration, figured out what consents you needed, and then asked for all of the consents not yet granted. It doesn't require you to include the permissions that you need in your code because they are in your app registration.

## Becoming a Verified Publisher

Microsoft customers sometimes describe difficulty in deciding when to allow an application to access the Microsoft identity platform by signing in a user or calling an API. They want increased visibility and control, more proactive and easier reactive decisions, systems that keep data safe and reduce the decision burden, and accelerated app adoption for trustworthy developers. In adopting [Zero Trust principles](../zero-trust-overview.md), they are restricting consent to apps with low-risk permissions that are publisher verified. While access to data in APIs like Microsoft Graph allows you to build rich applications, your organization or your customer will evaluate the permissions that your app requests along with your app's trustworthiness. This affects you, as a developer.

Becoming a [Microsoft Verified Publisher](/azure/active-directory/develop/publisher-verification-overview) helps you to give your customers an easier experience in accepting your application requests. When an application comes from a verified publisher, users, IT Pros, and customers know that it comes from someone with whom Microsoft has a business relationship. A blue checkmark appears next to the publisher's name (component #5 in the **Permissions requested** consent prompt example below; see component table at [Azure AD application consent experience](/azure/active-directory/develop/application-consent-experience#building-blocks-of-the-consent-prompt)). The user can select the verified publisher from the consent prompt to view more information.

:::image type="complex" source="../media/screenshot-application-permissions-requested-consent-prompt-inline.png" alt-text="Screenshot of Permissions requested dialog shows component building blocks as described in linked Azure AD application consent experience article." lightbox="../media/screenshot-application-permissions-requested-consent-prompt-expanded.png":::
   "Screenshot of the consent experience Permissions requested dialog shows component building blocks as described in linked Azure AD application consent experience article. Emphasized is component number 5 which is the name of the verified publisher and a blue checkmark that the user can click to get more information about the publisher."
:::image-end:::

When you're a verified publisher, users and IT pros gain trust in your application because you are a verified entity. Publisher verification provides improved branding for your application, as well as increased transparency, reduced risk, and smoother enterprise adoption for your
customers.

## Next steps

- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to determine your application permission approach to credential management.
- [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) will help you to understand best practices for your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md).
- [Security best practices for application properties](/azure/active-directory/develop/security-best-practices-for-app-registration) describes redirect URI, access tokens (used for implicit flows), certificates and secrets, application ID URI, and application ownership.
