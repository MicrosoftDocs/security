---
title: Supported identity and account types for single- and multi-tenant apps
description: In this article, we explain how developers can determine, during app registration, which users their app allows from single- and multi-tenants.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 07/28/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to understand how to determine which users my app allows, during app registration, from single tenants and multi-tenants.
---
# Identity and account types for single- and multi-tenant apps

This article will explain how you, as a developer, can choose if your app allows only users from your Azure Active Directory (Azure AD) tenant, any Azure AD tenant, or users with personal Microsoft accounts. You can configure your app to be either [single tenant or multitenant](/azure/active-directory/develop/single-and-multi-tenant-apps) during [app registration](/azure/active-directory/develop/quickstart-register-app) in Azure. Ensure the [Zero Trust](overview.md) principle of least privilege access so that your app only requests permissions it needs.

The Microsoft identity platform provides support for specific [identity types](identity-supported-account-types.md):

- Work or school accounts when the entity has an account in an Azure Active Directory (AD)
- Microsoft personal accounts (MSA) for anyone who has account in Outlook.com, Hotmail, Live, Skype, Xbox, etc.
- [External identities](/azure/active-directory/external-identities/) in Azure AD for partners (users outside of your organization)
- [Azure AD Business to Customer (B2C)](/azure/active-directory-b2c/overview) that allows you to create a solution that will let your customers bring in their other identity providers. Applications that use Azure AD B2C or are subscribed to [Microsoft Dynamics 365 Fraud Protection with Azure Active Directory B2C](/azure/active-directory-b2c/partner-dynamics-365-fraud-protection) can assess potentially fraudulent activity following attempts to create new accounts or sign in to the client's ecosystem.

A required part of application registration in Azure AD is your selection of supported account types. While IT Pros in administrator roles decide who can consent to apps in their tenant, you, as a developer, specify who can use your app based on account type. When a tenant doesn't allow you to register your application in Azure AD, administrators will provide you with a way to communicate those details to them through another mechanism.

You'll choose from the following supported account type options when registering your application.

- `Accounts in this organizational directory only (O365 only - Single tenant)`
- `Accounts in any organizational directory (Any Azure AD directory - Multitenant)`
- `Accounts in any organizational directory (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)`
- `Personal Microsoft accounts only`

## Accounts in this organizational directory only - single tenant

When you select **Accounts in this organizational directory only (O365 only - Single tenant)**, you allow only users and guests from the tenant where the developer has registered their app. This option is the most common for Line of Business (LOB) applications.

## Accounts in any organizational directory only - multitenant

When you select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**, you allow any user from any Azure AD directory to sign in to your multi-tenant application. If you want to only allow users from specific tenants, you'll filter these users in your code by checking that the [tid claim in the id_token](/azure/active-directory/develop/id-tokens) is on your allowed list of tenants. Your application can use the organizations endpoint or the common endpoint to sign in users in the user's home tenant. To support guest users signing in to your multitenant app, you'll use the specific tenant endpoint for the tenant where the user is a guest to sign in the user.

## Accounts in any organizational account and personal Microsoft accounts

When you select **Accounts in any organizational account and personal Microsoft accounts (Any Azure AD directory - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)**, you allow a user to sign in to your application with their native identity from any Azure AD tenant or consumer account. The same tenant filtering and endpoint usage apply to these apps as they do to multitenant apps as described above.

## Personal Microsoft accounts only

When you select **Personal Microsoft accounts only**, you allow only users with consumer accounts to use your app.

## Customer facing applications

When you build a solution in the Microsoft identity platform that reaches out to your customers, usually you don't want to use your corporate directory. Instead, you want the customers to be in a separate directory so that they can't access any of your company's corporate resources. To fulfill this need, Microsoft offers [Azure AD Business to Customer (B2C)](/azure/active-directory-b2c/overview).

Azure AD B2C provides business-to-customer identity as a service. You can allow users to have a username and password just for your app. B2C supports customers with social identities to reduce passwords. You can support enterprise customers by federating your Azure AD B2C directory to your customers' Azure AD (or any identity provider that supports SAML) to OpenID Connect. Unlike a multitenant app, your app doesn't use the customer's corporate directory where they're protecting their corporate assets. Your customers can access your service or capability without granting your app access to their corporate resources.

## It's not just up to the developer

While you define in your application registration who can sign in to your app, the final say comes from the individual user or the admins of the user's home tenant. Tenant admins often want to have more control over an app than just who can sign in. For example, they may want to apply a Conditional Access policy to the app or control which group they allow to use the application. To enable tenant admins to have this control, there's a second object in the Microsoft identity platform: the Enterprise app. Enterprise apps are also known as [Service Principals](/azure/active-directory/develop/app-objects-and-service-principals).

## For apps with users in other tenants or other consumer accounts

As shown in the diagram below using an example of two tenants (for the fictitious organizations, Adatum and Contoso), supported account types include the **Accounts in any organizational directory** option for a multi-tenant application so that you can allow organizational directory users. In other words, you'll allow a user to sign in to your application with their native identity from any Azure AD. A Service Principal is automatically created in the tenant when first user from a tenant authenticates to the app.

:::image type="complex" source="../media/develop/identity-supported-account-types/diagram-multitenant-app-allows-org-directory-users-inline.gif" alt-text="Diagram shows how a multitenant application can allow organizational directory users." lightbox="../media/develop/identity-supported-account-types/diagram-multitenant-app-allows-org-directory-users-expanded.gif":::
   The animated GIF shows two diagrams with a motion transition between the first diagram and the second diagram. First diagram title: Service Principal automatically created in tenant when first user from a tenant authenticates to the app. Below the first diagram title, on the left, are two bullet points: Only one application registration, or application object. Enterprise app, Service Principal, in every tenant that allows the user to sign in to the app. To the left of the bullet points, a cloud shape represents the Adatum tenant where Adatum is the name of a fictitious organization. Inside the Adatum tenant cloud shape, an icon represents the App and another icon represents the Adatum SP. An arrow connects the App icon to the SP icon. Second diagram title: Tenant admin controls how the app works in their tenant with the Enterprise app for that app. Below the second diagram title, on the left, a cloud shape represents the Adatum tenant where Adatum is the name of a fictitious organization. To the right of the Adatum cloud shape, another cloud shape represents the Contoso tenant where Contoso is the name of a fictitious organization. Inside the Contoso cloud shape, an icon represents the Contoso SP. An arrow connects Adatum app inside of the Adatum cloud shape to the Contoso SP inside of the Contoso cloud shape.
:::image-end:::

There's only one application registration or application object. However, an Enterprise app, or Service Principal (SP), in every tenant allows users to sign in to the app. The tenant admin can control how the app works in their tenant.

## Multitenant app considerations

Multitenant apps sign in users from the user's home tenant when the app uses the common or organization endpoint. The app has one app registration as shown in the diagram below. In this example, the application is registered in the Adatum tenant. User A from Adatum and User B from Contoso can both sign into the app with the expectation User A from Adatum will access Adatum data and that User B from Contoso will access Contoso data.

:::image type="complex" source="../media/develop/identity-supported-account-types/diagram-multitenant-app-common-endpoint-inline.png" alt-text="Diagram shows how multitenant apps sign in users from user's home tenant when app uses common or organization endpoint." lightbox="../media/develop/identity-supported-account-types/diagram-multitenant-app-common-endpoint-expanded.png":::
      Diagram title: Multitenant App vs. External Identities, also known as B 2 B. On the left, 'Adatum' appears above a building to represent the Adatum organization where Adatum is the name of a fictitious organization. On the right, 'Contoso' appears above a building to represent the Contoso organization where Contoso is the name of a fictitious organization. To the right of the Adatum building is a box with the title, Adatum App Registration. It contains an icon that represents the Adatum Data on the left and an icon that represents the Contoso Data on the right. An arrow connects the Adatum building to the Adatum App Registration box. Inside the Adatum building, a circle represents User A. An arrow connects User A to the Adatum App Registration box. Inside of the Contoso building, a circle represents User B. An arrow connects User B to the Adatum App Registration box. Text at the bottom of the diagram, between the two buildings: Multitenant app. Uses common endpoint to sign in. No invitation/external account needed.
:::image-end:::

As a developer, it's your responsibility to keep tenant information separate. For example, if the Contoso data is from Microsoft Graph, the User B from Contoso will only see Contoso's Microsoft Graph data. There's no possibility for User B from Contoso to access Microsoft Graph data in the Adatum tenant because Microsoft 365 has true data separation.

In the above diagram, User B from Contoso can sign in to the application and they can access Contoso data in your application. Your application can use our common (or organization) endpoints so the user signs in natively to their tenant, requiring no invitation process. A user can run and sign in to your application and it will work after the user or tenant admin grants consent.

## Collaboration with external users

When enterprises want to enable users who aren't members of the enterprise to access data from the enterprise, they use the [Azure AD Business to Business (B2B)](/azure/active-directory/external-identities/b2b-fundamentals) feature. As illustrated in the diagram below, enterprises can invite users to become guest users in their tenant. After the user accepts the invitation, they can access data that the inviting tenant has protected. The user doesn't create a separate credential in the tenant.

:::image type="complex" source="../media/develop/identity-supported-account-types/diagram-multitenant-app-external-identities-inline.png" alt-text="Diagram shows how enterprises invite guest users to their tenant." lightbox="../media/develop/identity-supported-account-types/diagram-multitenant-app-external-identities-expanded.png":::
      Diagram title: Multitenant App vs. External Identities, also known as B 2 B. On the left, 'Adatum' appears above a building to represent the Adatum organization. On the right, 'Contoso' appears above a building to represent the Contoso organization. Inside of the Contoso building is a circle that represents User B. To the right of the Adatum building, a box containing an icon represents the Adatum Data and App Registration. An arrow connects the Adatum building to the data and registration box. Inside of the Adatum building, a circle represents User A. An arrow connects User A to the data and registration box. A smaller circle inside of the Adatum building connects with an arrow to User B and with another arrow to the data and registration box. Text at the bottom of the diagram, between the two buildings: External Identities. Use Adatum endpoint to sign in. Can't use common endpoint. Invitation/external account needed.
:::image-end:::

Guest users authenticate by signing in to their home tenant, personal Microsoft Account, or other IDP account. Guests can also authenticate with a one-time passcode using any email. After guests authenticate, the inviting tenant's Azure AD provides a token for access to inviting tenant's data.

As a developer, keep these considerations in mind when your application supports guest users:

- You must use a tenant specific endpoint when signing in the guest user. You can't use the common, organization, or consumer endpoints.
- The guest user identity is different from the user's identity in their home tenant or other IDP. The `oid` claim in the token for a guest user will be different from the same individual's `oid` in their home tenant.

## Next steps

- [How and why apps are added to Azure AD](/azure/active-directory/develop/active-directory-how-applications-are-added) explains how application objects describe an application to Azure AD.
- [Security best practices for application properties in Azure Active Directory](/azure/active-directory/develop/security-best-practices-for-app-registration) covers properties such as redirect URI, access tokens, certificates and secrets, application ID URI, and application ownership.
- [Building apps with a Zero Trust approach to identity](identity.md) provides an overview of permissions and access best practices.
- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Developing delegated permissions strategy](developer-strategy-delegated-permission.md) helps you to implement the best approach for managing permissions in your application and develop using Zero Trust principles.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
