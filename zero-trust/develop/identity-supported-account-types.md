---
title: Supported identity and account types for single- and multi-tenant apps
description: In this article, we explain how developers can determine, during app registration, which users their app allows from single tenants and multitenants.
author: janicericketts
ms.author: jricketts
ms.service: security
ms.topic: conceptual
ms.date: 07/27/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand how to determine which users my app allows, during app registration, from single tenants and multitenants.
---
# Identity and account types for single- and multi-tenant apps

This article will explain how you, as a developer, can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts by configuring your app to be either single tenant or multitenant during app registration in Azure and ensure the [Zero Trust](../zero-trust-overview.md) principle of least privilege access so that your app only requests permissions it needs.

The Microsoft identity platform provides support for specific [identity types](/azure/active-directory/develop/single-and-multi-tenant-apps):

- Work or school accounts when the entity has an account in an Azure Active Directory (AD)

- Microsoft personal accounts (MSA ) for anyone who has account in outlook.com, Hotmail, Live, Skype, Xbox, etc.

- [External identities](/azure/active-directory/external-identities/) in Azure AD for partners (users outside of your organization)

- [Azure AD Business to Customer (B2C)](/azure/active-directory-b2c/overview) that allows you to create a solution that will let your customers bring in their other identities providers.

A required part of application registration in Azure AD is your [selection of supported account types](/azure/active-directory/develop/quickstart-register-app). While IT Pros in administrator roles decide who can consent to apps in their tenant, you, as a developer, specify who can use your app based on account type. When a tenant does not allow you to register your application in Azure AD, administrators will provide you with a way to communicate those details to them through another mechanism.

You will choose from the following supported account type options when registering your application.

- Accounts in this organizational directory only (O365 only - Single tenant)

- Accounts in any organizational directory (Any Azure AD directory - Multitenant)

- Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)

- Personal Microsoft accounts only

## Accounts in this organizational directory only - single tenant

When you select **Accounts in this organizational directory only (O365
only - Single tenant)**, you allow only users and guests from the tenant
where the developer has registered their app. This is the most common
choice for Line of Business (LOB) applications.

## Accounts in any organizational directory only - multitenant

When you select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**, you allow any user from any Azure AD directory to sign into your multi-tenant application. If you want to only allow users from specific tenants, you will filter these users in your code by checking that the [tid claim in the id_token](/azure/active-directory/develop/id-tokens) is on your allowed list of tenants. Your application can use the organizations endpoint or the common endpoint to sign in users in the user's home tenant. To support guest users signing in to your multitenant app, you will use the specific tenant endpoint for the tenant where the user is a guest to sign in the user.

## Accounts in any organizational account and personal Microsoft accounts

When you select **Accounts in any organizational account and personal Microsoft accounts (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)**, you allow a user to sign into your application with their native identity from any Azure AD tenant or consumer account. The same tenant filtering and endpoint usage apply to these apps as they do to multitenant apps as described above.

## Personal Microsoft accounts only

When you select **Personal Microsoft accounts only**, you allow only users with consumer accounts to use your app.

## Customer facing applications

When you build a solution in the Microsoft identity platform that reaches out to your customers, usually you do not want to use your corporate directory. Instead, you want the customers to be in a separate directory so that they cannot access any of your company's corporate resources. To fulfill this need, Microsoft offers [Azure AD Business to Customer (B2C)](/azure/active-directory-b2c/overview).

Azure Active Directory B2C provides business-to-customer identity as a service. In addition to enabling your app users to have a username and password just for your app, B2C enables you to support customers with the social identity that you allow them to bring so that they don't have to remember more passwords. For example, you can allow users to use their Facebook or Twitter ID. You can also support enterprise customers by federating your Azure AD B2C directory to your customers' Azure AD (or any identity provider (IDP) that supports SAML) to OpenID Connect. Unlike a multitenant app, your app does not use the customer's corporate directory where they are protecting their corporate assets. B2C allows your customers to access your service or capability without granting your app access to their corporate resources.

## It is not just up to the developer

While you, as the developer, define in your application registration who you will allow to sign into your app, you do not have the final say on whether any specific user, or users from a specific tenant, can sign into your app. The final say comes from the individual user or the admins of the user's home tenant. Tenant admins often want to have more control over an app than just who can sign in. For example, they may want to apply a Conditional Access policy to the app or control which group they allow to use the application. To enable tenant admins to have this control, there is a second object in the Microsoft identity platform: the Enterprise app. Enterprise apps are also known as [Service Principals](/azure/active-directory/develop/app-objects-and-service-principals).

## For apps with users in other tenants or other consumer accounts

As shown in the diagram below using an example of two tenants (for the fictitious organizations, Adatum and Contoso), supported account types include the **Accounts in any organizational directory** option for a multi-tenant application so that you can allow organizational directory users. In other words, you will allow a user to sign into your application with their native identity from any Azure AD. A Service Principal is automatically created in the tenant when first user from a tenant authenticates to the app.

:::image type="content" source="../media/diagram-multitenant-app-allows-org-directory-users.gif" alt-text="diagram illustrates multitenant application that can allow organizational directory users" lightbox="../media/diagram-multitenant-app-allows-org-directory-users.gif":::

There is only one application registration, or application object, but there is an Enterprise app, or Service Principal (SP), in every tenant that allows the user to sign into the app. The tenant admin can control how the app works in their tenant with the Enterprise app for that app.

## Multitenant app considerations

Multitenant apps sign in users from the user's home tenant when the app uses the common or organization endpoint. The app has one app registration as shown in the diagram below. In this example, the application is registered in the Adatum tenant. User A from Adatum and User B from Contoso can both sign in to the app with the expectation User A from Adatum will access Adatum data and that User B from Contoso will access Contoso data.

:::image type="content" source="../media/diagram-multitenant-app-common-endpoint.png" alt-text="diagram illustrates multitenant apps sign in users from user's home tenant when app uses common or organization endpoint" lightbox="../media/diagram-multitenant-app-common-endpoint.png":::

As a developer, it is your responsibility to keep tenant information separate. For example, if the Contoso data is from Microsoft Graph, the User B from Contoso will only see Contoso's Microsoft Graph data. There's no possibility for User B from Contoso to access Microsoft Graph data in the Adatum tenant because Microsoft 365 has true data separation.

In the above diagram, User B from Contoso can sign into the application and they can access Contoso data in your application. Your application can use our common, or organization, endpoints, so the user signs in natively to their tenant, wherever that tenant is, and there's no invitation process required. A user can simply run and sign into your application and it will work after the user or tenant admin grants consent.

## Collaboration with external users

When enterprises want to enable users who are not members of the enterprise to access data from the enterprise, the [Azure AD Business to Business (B2B)](/azure/active-directory/external-identities/b2b-fundamentals) feature makes this possible. As illustrated in the diagram below, enterprises can invite users to become guest users in their tenant. After the user accepts the invitation, they can access data that the inviting tenant has protected. The user does not create a separate credential in the tenant.

:::image type="content" source="../media/diagram-multitenant-app-external-identities.png" alt-text="diagram illustrates enterprises invite guest users to their tenant" lightbox="../media/diagram-multitenant-app-external-identities.png":::

When a guest user needs to authenticate, they sign in to their home tenant, a personal Microsoft Account, an account from a different IDP, or with a one-time passcode using any email account. After they have authenticated with their IDP, the inviting tenant's Azure AD provides the application with a token that identifies them as a guest user in the tenant. This guest user can then access the data in the inviting tenant.

As a developer, keep these considerations in mind when your application supports guest users:

- You must use a tenant specific endpoint when signing in the guest user. You cannot use the common, organization, or consumer endpoints.

- The guest user identity is different from the user's identity in their home tenant or other IDP. This means that the oid claim in the token for a guest user will be different from the same individual's oid in their home tenant.

## Next steps

- [How and why apps are added to Azure AD - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/active-directory-how-applications-are-added) explains how application objects describe the application to Azure AD that issues tokens to the application based on its settings.

- [Supported account types - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/v2-supported-account-types) describes the account types (sometimes called audiences) that Microsoft identity platform applications support.

- [Single and multi-tenant apps in Azure AD - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/single-and-multi-tenant-apps) shows how Azure AD organizes objects like users and apps into groups called tenants where administrators set policies to meet security and operational policies.

- [Best practices for Azure AD application registration configuration - Microsoft Entra \| Microsoft Docs](/azure/active-directory/develop/security-best-practices-for-app-registration) describes security best practices for application properties such as redirect URI, access tokens (used for implicit flows), certificates and secrets, application ID URI, and application ownership.
