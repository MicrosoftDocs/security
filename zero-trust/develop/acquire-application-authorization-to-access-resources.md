---
title: Acquiring authorization to access resources
description: As a developer, learn how to best ensure Zero Trust when acquiring resource access permissions for your application.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 12/13/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand how to best ensure Zero Trust when acquiring resource access permissions for my application.
---
# Acquiring authorization to access resources

This article will help you, as a developer, to understand how to best ensure [Zero Trust](overview.md) when acquiring resource access permissions for your application. To access protected resources like email or calendar data, your application needs the resource owner's *authorization*. The resource owner can *consent* to or deny your app's request. Your app will receive an access token when the resource owner grants consent; your app won't receive an access token when the resource owner denies access.

## Conceptual review

You can use the Microsoft identity platform to [authenticate and authorize](/azure/active-directory/develop/authentication-vs-authorization) your applications and manage [permissions and consent](/azure/active-directory/develop/permissions-consent-overview). Let's start with some concepts:

- *Authentication* (sometimes shortened to *AuthN*) is the process of proving that your claimed identity is accurate. The Microsoft identity platform uses the [OpenID Connect](https://openid.net/connect/) protocol for handling authentication. *Authorization* (sometimes shortened to *AuthZ*) grants an authenticated party permission to do something. It specifies what data the authenticated party can access. The Microsoft identity platform uses the [OAuth2.0](https://oauth.net/2/) protocol for handling authorization. [Authorization options](/azure/active-directory/develop/authorization-basics) include access control lists (ACL), role-based access control, and attribute access control (ABAC). Authentication is often a factor of authorization.

- To access data, your application can use *delegated access* (acting on behalf of a signed-in user) or *direct access* (acting only as the application's own identity). [Delegated access](/azure/active-directory/develop/permissions-consent-overview#delegated-access-access-on-behalf-of-a-user) requires delegated permissions (also known as [scopes](/azure/active-directory/develop/v2-permissions-and-consent#scopes-and-permissions)); the client and the user must be separately authorized to make the request. [Direct access](/azure/active-directory/develop/permissions-consent-overview#direct-access-app-only-access) may require application permissions (also known as [app roles](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps)); when app roles are granted to applications, they can be called applications permissions.

- *Delegated permissions*, used with delegated access, allow an application to act on behalf of a user, accessing only what the user can access. *Application permission*,  used with direct access, allow an application to access any data with which the permission is associated. Only administrators and owners of [service principals](/azure/active-directory/develop/active-directory-how-applications-are-added#what-are-service-principals-and-where-do-they-come-from) can consent to application permissions.

- Applications receive permissions through *consent*; users or admins authorize an application to access a protected resource. A [consent prompt](/azure/active-directory/develop/application-consent-experience) lists the permissions that the application requires along with publisher information.

- Resource application owners can *preauthorize* client apps (in the Azure portal or by using PowerShell and APIs like Microsoft Graph). They can grant resource permissions without requiring users to see a consent prompt for the set of permissions that have been [preauthorized](/azure/active-directory/develop/permissions-consent-overview#preauthorization).

## Difference between delegated and application permission

Applications work in two modes: when a user is present (delegated permission) and [when there's no user](identity-non-user-applications.md) (application permission). When there's a user in front of an application, you're compelled to act on behalf of that user; you shouldn't be acting on behalf of the application itself. When a user is directing your application, you're acting as the delegate for that user. You're getting permission to act on behalf of the user that the token identifies.

Service type applications (background tasks, daemons, server-to-server processes) don't have users who can identify themselves or type in a password. They require an application permission to act on behalf of itself (on behalf of the service application).

## Zero Trust application authorization best practices

Your [authorization approach](/azure/active-directory/develop/authorization-basics) will have authentication as a component when you connect to a user present to the application and to the resource you're calling. When your application is acting on behalf of a user, we don't trust a calling application to tell us who the user is or let the application decide who the user is. Azure AD will verify and directly provide information about the user in the token.

When you need to allow your application to call an API or authorize your application so that the application can access a resource, modern authorization schemes can require authorization through a [permission and consent framework](/azure/active-directory/develop/consent-framework). Reference [Security best practices for application properties](/azure/active-directory/develop/security-best-practices-for-app-registration) that include redirect URI, access tokens (used for implicit flows), certificates and secrets, application ID URI, and application ownership.

## Next steps

- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
- [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
- [Providing application identity credentials when there's no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure resources.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
- [Building apps with a Zero Trust approach to identity](identity.md) continues from the [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) article to help you use a Zero Trust approach to identity in your software development Lifecycle (SDLC).
