---
title: Example of API protected by Microsoft identity consent framework
description: Design a permissions and consent strategy that provides the best user experience when you implement least privilege.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 09/12/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to to design a permissions and consent strategy so that I can provide the best user experience when I implement least privilege.
---
# Example of API protected by Microsoft identity consent framework

This article can help you, as a developer, to design your [application permissions strategy](developer-strategy-application-permissions.md) to provide [least privilege](overview.md). Before proceeding, see the [API protection](protect-api.md) article to learn best practices for registration, defining permissions and consent, and enforcing access.

Let's take a look at how an API that is protected by the Microsoft identity platform uses the [Microsoft identity consent framework](/azure/active-directory/develop/consent-framework). We'll use the Microsoft Graph API as our example because it makes the most extensive use of the Microsoft identity platform consent framework.

## Naming convention for permission names

The Microsoft Graph team created a naming convention for permission names to make it easier to connect the permission to the resource access that the permission enables. [Microsoft Graph permission names](/graph/permissions-reference#microsoft-graph-permission-names) adhere to a simple *resource.operation.constraint* pattern. The two primary operations are *Read* and *ReadWrite* (which includes update and delete).

The *constraint* element affects the degree of access that your app has within the directory. Microsoft Graph supports these constraints:

- *All* grants permission for your app to perform the operations on all of the resources of the specified type in a directory.
- *Shared* grants permission for your app to perform the operations on resources that other users have shared with the signed-in user.
- *AppFolder* grants permission for your app to read and write files in a dedicated folder in OneDrive. This constraint is exposed only on the [Files permissions](/graph/permissions-reference#files-permissions) object and is only valid for Microsoft accounts.
- If you specify *No constraint*, your app can only perform the operations on the resources that the signed-in user owns.

## Access and operations against specific resources

Let's look at some permissions, or scopes, for the user object in Microsoft Graph to see how the Microsoft API designers enabled specific access and operations against specific resources:

|Permission        |Display String                         |Description|
|------------------|---------------------------------------|-----------|
|`User.Read`       |Sign-in and read user profile          |Allows users to sign-in to the app and allows the app to read the profile of signed-in users. It also allows the app to read basic company information of signed-in users.|
|`User.ReadWrite`  |Read and write access to user profile  |Allows the app to read the signed-in user's full profile. It also allows the app to update the signed-in user's profile information on their behalf.|

`User.Read` and `User.ReadWrite` exist (as opposed to a single permission like `User.Access` that doesn't exist) so that applications can follow the [Zero Trust](overview.md) principle of least privilege. If the developer doesn't have a requirement and code to update the user's profile, the app won't ask for `User.ReadWrite`. Therefore, an attacker can't compromise the application and use it to change data.

Notice that `User.Read` doesn't just give the application access to the user object. Each permission represents a specific range of operation. It's important that developers and admins read the permission description to see exactly what any specific permission enables. `User.Read`, in addition to enabling reading the current user's full profile, enables the application to see the basic information from the [Organizations](/graph/api/organization-get) object in Microsoft Graph.

Let's look at another permission:

|Permission             |Display String                         |Description|
|-----------------------|---------------------------------------|-----------|
|`User.ReadBasic.All`   |Read all users' basic profiles         |Allows the app to read a basic set of profile properties of other users in your organization on behalf of the signed-in user. Includes display name, first and last name, email address, open extensions, and photo. Allows the app to read the full profile of the signed-in user.|

The range of operation that `User.ReadBasic.All` starts with everything that `User.Read` does. In addition, you can access display name, first and last name, email address, photo, and  open extensions for other organization users. The specific range of operation enables applications to have a nice people picker UI and is an example of the API designers using a permission to enable a specific range of operation.

Let's look at a couple more permissions on the Microsoft Graph user object:

|Permission            |Display String                         |Description|
|----------------------|---------------------------------------|-----------|
|`User.Read.All`       |Read all users' full profiles          |Allows the app to read the full set of profile properties, reports, and managers of other users in your organization, on behalf of the signed-in user.|
|`User.ReadWrite.All`  |Read and write all users' full profiles|Allows the app to read and write the full set of profile properties, reports, and managers of other users in your organization, on behalf of the signed-in user. Also allows the app to create and delete users and reset user passwords on behalf of the signed-in user.|

As with `User.Read` and `User.ReadWrite`, `User.Read.All` and `User.ReadWrite.All` are distinct permissions that enable an application to follow the least privilege Zero Trust principle.

`User.Read.All` is interesting because every user in the organization has this capability (for example, open Outlook, go up and down a reporting chain). You, as an individual, can see the full user profile of every other user in your organization. However, the Microsoft Graph API designers decided that only admins should allow an application to perform the same operation because `User.Read.All` includes the tenant's organizational hierarchy. If a bad actor accessed this information, they could mount a targeted phishing attack where the phishing email came from a person's manager or their manager's manager.

`User.ReadWrite.All` is a powerful range of operation. An application granted this permission can update, or even delete, every user in the tenant. As a [delegated permission](developer-strategy-delegated-permission.md), when a user is in front of the app, the app can do only what the current user can do. Regular users can't update or delete other users regardless of the app's permissions. However, when a tenant admin uses the app, then they can perform these operations. When deciding to grant or deny this permission, you should evaluate your app with a tenant admin user in mind.

## Permissions requiring admin consent

Given the power of `User.Read.All` and `User.ReadWrite.All`, the Microsoft Graph API designers designated these permissions as requiring admin consent. Let's add an **Admin?** Column to our table of permissions to indicate when the permission requires admin consent:

|Permission|Display String|Description|Admin?|
|----------|--------------|-----------|------|
|`User.Read`|Sign-in and read user profile|Allows users to sign-in to the app and allows the app to read the profile of signed-in users. It also allows the app to read basic company information of signed-in users.|**No**|
|`User.ReadWrite`|Read and write access to user profile|Allows the app to read the signed-in user's full profile. It also allows the app to update the signed-in user's profile information on their behalf.|**No**|
|`User.ReadBasic.All`|Read all users' basic profiles|Allows the app to read a basic set of profile properties of other users in your organization on behalf of the signed-in user. Includes display name, first and last name, email address, open extensions, and photo. Allows the app to read the full profile of the signed-in user.|**No**|
|`User.Read.All`|Read all users' full profiles|Allows the app to read the full set of profile properties, reports, and managers of other users in your organization, on behalf of the signed-in user.|**Yes**|
|`User.ReadWrite.All`|Read and write all users' full profiles|Allows the app to read and write the full set of profile properties, reports, and managers of other users in your organization, on behalf of the signed-in user. Also allows the app to create and delete users and reset user passwords on behalf of the signed-in user.|**Yes**|

As demonstrated in the [Requesting permissions that require administrative consent](permissions-require-admin-consent.md) article, tenant admins can overrule requirements and designate any or all application permissions in their tenant as requiring admin consent. You're wise to design your app to gracefully handle when you don't receive a token from your request. Lack of consent is one of many reasons that your app may not receive a token.

## Next steps

- [Calling an API from another API](api-calls-api.md) helps you to ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
- [Requesting permissions that require administrative consent](permissions-require-admin-consent.md) describes the permission and consent experience when application permissions will require administrative consent.
- In this [Quickstart: Protect a web API with the Microsoft identity platform](/azure/active-directory/develop/web-api-quickstart?pivots=devlang-aspnet), download and run a code sample that demonstrates how to protect an ASP.NET web API.
- In this [Tutorial - Transform and protect your API in Azure API Management](/azure/api-management/transform-api), learn about configuring common policies to hide technology stack info and original URLs in the API HTTP response body.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
