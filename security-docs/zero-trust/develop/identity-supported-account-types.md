---
title: Identity and account types for single- and multitenant apps
description: In this article, we explain how developers can determine, during app registration, which users their app allows from single- and multitenants.
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.service: zero-trust
ms.date: 04/18/2025
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to understand how to determine which users my app allows, during app registration, from single tenants and multi-tenants.
---
# Identity and account types for single- and multitenant apps

This article explains how you, as a developer, can choose if your app allows only users from your Microsoft Entra tenant, any Microsoft Entra tenant, or users with personal Microsoft accounts. You can configure your app to be either [single tenant or multitenant](/entra/identity-platform/single-and-multi-tenant-apps) during [app registration](/entra/identity-platform/quickstart-register-app) in Microsoft Entra. Ensure the [Zero Trust](overview.md) principle of least privilege access so that your app only requests permissions it needs.

The Microsoft identity platform provides support for specific [identity types](identity-supported-account-types.md):

- Work or school accounts when the entity has an account in a Microsoft Entra ID.
- Microsoft personal accounts (MSA) for anyone who has account in Outlook.com, Hotmail, Live, Skype, Xbox, etc.
- [External identities](/entra/external-id/) in Microsoft Entra ID for partners (users outside of your organization).

A required part of application registration in Microsoft Entra ID is your selection of supported account types. While IT Pros in administrator roles decide who can consent to apps in their tenant, you, as a developer, specify who can use your app based on account type. When a tenant doesn't allow you to register your application in Microsoft Entra ID, administrators provide you with a way to communicate those details to them through another mechanism.

You choose from the following supported account type options when registering your application.

- `Accounts in this organizational directory only (O365 only - Single tenant)`
- `Accounts in any organizational directory (Any Azure AD directory - Multitenant)`
- `Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)`
- `Personal Microsoft accounts only`

## Accounts in this organizational directory only - single tenant

When you select **Accounts in this organizational directory only (O365 only - Single tenant)**, you allow only users and guests from the tenant where the developer registered their app. This option is the most common for Line of Business (LOB) applications.

## Accounts in any organizational directory only - multitenant

When you select **Accounts in any organizational directory (Any Microsoft Entra directory - Multitenant)**, you allow any user from any Microsoft Entra directory to sign in to your multitenant application. If you want to only allow users from specific tenants, you filter these users in your code by checking that the [tid claim in the id_token](/entra/identity-platform/id-tokens) is on your allowed list of tenants. Your application can use the organizations endpoint or the common endpoint to sign in users in the user's home tenant. To support guest users signing in to your multitenant app, you use the specific tenant endpoint for the tenant where the user is a guest to sign in the user.

## Accounts in any organizational account and personal Microsoft accounts

When you select **Accounts in any organizational account and personal Microsoft accounts (Any Microsoft Entra directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)**, you allow a user to sign in to your application with their native identity from any Microsoft Entra tenant or consumer account. The same tenant filtering and endpoint usage apply to these apps as they do to multitenant apps as previously described.

## Personal Microsoft accounts only

When you select **Personal Microsoft accounts only**, you allow only users with consumer accounts to use your app.

## It's not just up to the developer

While you define in your application registration who can sign in to your app, the final say comes from the individual user or the admins of the user's home tenant. Tenant admins often want to have more control over an app than just who can sign in. For example, they might want to apply a Conditional Access policy to the app or control which group they allow to use the application. To enable tenant admins to have this control, there's a second object in the Microsoft identity platform: the Enterprise app. Enterprise apps are also known as [Service Principals](/entra/identity-platform/app-objects-and-service-principals).

## Apps with users in other tenants or other consumer accounts

Supported account types include the **Accounts in any organizational directory** option for a multitenant application so that you can allow organizational directory users. In other words, you allow a user to sign in to your application with their native identity from any Microsoft Entra ID. A Service Principal is automatically created in the tenant when first user from a tenant authenticates to the app.

There's only one application registration or application object. However, there's an Enterprise app, or Service Principal (SP), in every tenant that allows users to sign in to the app. The tenant admin can control how the app works in their tenant.

## Multitenant app considerations

Multitenant apps sign in users from the user's home tenant when the app uses the common or organization endpoint. The app has one app registration as shown in the following diagram. In this example, the application is registered in the Adatum tenant. User A from Adatum and User B from Contoso can both sign into the app with the expectation User A from Adatum accesses Adatum data and that User B from Contoso accesses Contoso data.

:::image type="complex" source="../media/develop/identity-supported-account-types/diagram-multitenant-app-common-endpoint-inline.png" alt-text="Diagram shows how multitenant apps sign in users from user's home tenant when app uses common or organization endpoint." lightbox="../media/develop/identity-supported-account-types/diagram-multitenant-app-common-endpoint-expanded.png":::
      Diagram title: Multitenant App vs. External Identities, also known as B 2 B.
:::image-end:::

As a developer, it's your responsibility to keep tenant information separate. For example, if the Contoso data is from Microsoft Graph, the User B from Contoso only sees Contoso's Microsoft Graph data. There's no possibility for User B from Contoso to access Microsoft Graph data in the Adatum tenant because Microsoft 365 has true data separation.

In the diagram, User B from Contoso can sign in to the application and they can access Contoso data in your application. Your application can use the common (or organization) endpoints so the user natively signs in to their tenant, requiring no invitation process. A user can run and sign in to your application and it works after the user or tenant admin grants consent.

## Next steps

- [How and why apps are added to Microsoft Entra ID](/entra/identity-platform/how-applications-are-added) explains how application objects describe an application to Microsoft Entra ID.
- [Security best practices for application properties in Microsoft Entra ID](/entra/identity-platform/security-best-practices-for-app-registration) covers properties such as redirect URI, access tokens, certificates and secrets, application ID URI, and application ownership.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Acquire authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Develop delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
- [Develop application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
