---
title: Developing delegated permissions strategy
description: As a developer, implement the best approach for managing permissions in your application and develop using Zero Trust.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 08/31/2022
ms.custom: template-concept
# Customer intent: As a developer, I want to implement the best approach for managing permissions in my application and develop using Zero Trust.
---
# Developing delegated permissions strategy

This article will help you, as a developer, to implement the best approach for managing permissions in your application and [develop using Zero Trust principles](overview.md). As described in [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md), *delegated permissions* are used with delegated access to allow an application to act on behalf of a user, accessing only what the user can access. *Application permissions* are used with direct access to allow an application to access any data with which the permission is associated. Only administrators and owners of [service principals](/azure/active-directory/develop/active-directory-how-applications-are-added#what-are-service-principals-and-where-do-they-come-from) can consent to application permissions.

The permission and consent models refer primarily to an application. The permission and consent process has no control over what a user can do. It controls what actions the application is allowed to perform.

Referencing the following Venn diagram, with delegated permissions there's an intersection between what the user is allowed to do and what the application is allowed to do. That's the effective permission by which the application is bound. Any time you use a delegated permission, it's bounded by the effective permissions.

:::image type="complex" source="../media/diagram-effective-permissions-inline.png" alt-text="Venn diagram shows effective permissions as intersection of app permissions and user capabilities." lightbox="../media/diagram-effective-permissions-expanded.png":::
   "Venn diagram description: Left circle text: Apps are granted consent for the app's range of operation. Right circle text: Users have permissions for operations managed by their organization. Intersection of circles text: Effective permissions: intersection of app permissions and user capabilities."
:::image-end:::

For example, your application that has users in front of the app gets permission to update every user's profile in the tenant. That doesn't mean that anyone running your application can update anyone else's profile. If the admin decides to grant your application `User.ReadWrite.All`, then they believe that your application is doing the right things when updating any users profile. Your app might log the changes and properly safeguard the information. The admin makes a value judgment about the application, not about the user.

## Least privilege approach

APIs can be complex. Simple APIs may not have a lot of operations. Complex APIs like Microsoft Graph encapsulate many requests that an application may want to use. Just because the application has the right to read doesn't mean it should have the right to update. For example, Microsoft Graph has thousands of APIs; there's no reason that, just because you're allowed to read the user's profile, you are also allowed to delete all the user's OneDrive files.

As a developer, you are expected to know which APIs the app calls, understand the API documentation and what permissions are required, and use the least possible permission to accomplish your tasks. This the [Zero Trust](../zero-trust-overview.md) least privilege approach. APIs often provide access to organization data stores and attract the attention of attackers who want to access that data.

Evaluate the permissions you request to ensure that you seek the absolute least privileged set to get the job done. Avoid requesting higher privilege permissions; instead, carefully work through the large number of permissions that APIs like Microsoft Graph provide. Locate and use the minimum permissions to address your needs. If you won't write code to update the user's profile, you won't request it for your application. If you only access users and groups, you won't request access to other information in the directory. You won't request permission to manage user email if you won't write code that accesses user email.

It is important in Zero Trust application development to define your application's intention and what it needs to ensure that it can't be compromised and used in a way that you did not intend. An aspect of this is a request that somebody must approve in which you make a statement of what you require (e.g., read the user's mail).

## User and tenant administrator roles in permission and consent

People who can approve of your requests fall into two categories: admins who can always consent to permission requests and regular users who aren't admins. However, the tenant admins have the final say in their tenant regarding which permissions require admin consent and to which permissions a user can consent.

When an API designer requires admin consent for a permission, that permission will always require admin consent; a tenant admin can't overrule that and require only user consent.

When an API designer defines permissions that require user consent, user consent suggestions by the API designer can be overruled by the tenant admin. The tenant admins can do that with a "big switch" in the tenant: everything requires admin consent. They can overrule user consent in a more granular way with [permission and consent management](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal). For example, they may allow users to consent to user consent requests from [verified publishers](developer-strategy-authorization-best-practices.md#becoming-a-verified-publisher) but not from other publishers. In another example, they may allow User.Read to sign in the user and read their profile but require admin consent to apps that ask permission to mail or to files.

API designers make their suggestions but tenant admins have the final say. Therefore, as a developer, you won't always know when your app requires admin consent. It's nice to plan and design around that but remember, when you make a token request, it could be denied for any reason. In your code, you need to gracefully handle not getting a token because tenant admins in which your customers or users are running your application decide when permissions requires admin consent.

## Example using JavaScript MSAL

For the authentication in this example, you'll use our JavaScript Microsoft Authentication Library (MSAL) to sign in the user in a single page application (SPA) where all the app logic executes from the browser.

From the related [Quickstart article](/azure/active-directory/develop/single-page-app-quickstart?pivots=devlang-javascript), you can [download](/azure/active-directory/develop/single-page-app-quickstart?pivots=devlang-javascript#step-2-download-the-project) and run a code sample that demonstrates how a JavaScript single-page application (SPA) can sign in users and call Microsoft Graph using the authorization code flow with Proof Key for Code Exchange (PKCE). The code sample demonstrates how to get an access token to call the Microsoft Graph API or any web API.

As shown in the example code below, you'll instantiate a public client because an application that runs entirely in the browser must be a public client. The user can get their hands on the internals of your application when the code is in the browser.

```javascript
// Create the main myMSALObj instance
// configuration parameters are located at authConfig.js
const myMSALObj = new msal.PublicClientApplication(msalConfig);
```

Then you'll use our MSAL library. In MSAL JavaScript, there is a specific API to log in. There are two APIs that utilize specific capabilities within the browser. One is to log in with a pop-up experience; the other one is to log in with a browser redirect experience.

As shown in the code example below, the login pop-up handles the authentication that the user needs to perform by calling the login API.

```javascript
function signIn() {

    /**
     * You can pass a custom request object below. This will override the initial configuration. For more information, visit:
     * https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-browser/docs/request-response-object.md#request
     */

    myMSALObj.loginPopup(loginRequest)
        .then(handleResponse)
        .catch(error => {
            console.error(error);
        });
}
```

Your app can get information about the user, such as their display name r user ID. Next, your app needs get authorization to read the full profile of the user from Microsoft Graph. To do this, you will follow a pattern that you'll use throughout our MSAL libraries.

As shown in the example code below, your app attempts to get the authorization by calling `AcquireTokenSilent`. If Azure Active Directory (Azure AD) can issue the token without interacting with the user, then `AcquireTokenSilent` will return the token that your app needs to access Microsoft Graph on behalf of the user.

```javascript
function getTokenPopup(request) {

    /**
     * See here for more info on account retrieval: 
     * https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-common/docs/Accounts.md
     */
    request.account = myMSALObj.getAccountByUsername(username);
    
    return myMSALObj.`AcquireTokenSilent`(request)
        .catch(error => {
            console.warn("silent token acquisition fails. acquiring token using popup");
            if (error instanceof msal.InteractionRequiredAuthError) {
                // fallback to interaction when silent call fails
                return myMSALObj.`AcquireTokenPopup`(request)
                    .then(tokenResponse => {
                        console.log(tokenResponse);
                        return tokenResponse;
                    }).catch(error => {
                        console.error(error);
                    });
            } else {
                console.warn(error);   
            }
    });
}
```

However, often Azure AD cannot issue the token without interacting with the user. This might be because the user changed their password, they haven't granted consent, or other reasons. Therefore, `AcquireTokenSilent` will send an error back to the application it requires user interaction. When you're your app receives this, it will fall back to call `AcquireTokenPopup`.

At that point, Azure AD will have a conversation with the user so they can do an MFA, provide their password, grant consent, or whatever action is needed to authenticate the user and authorize your app to act on the user's behalf. Then your app will get the token needed to move forward.

A primary step in an enterprise's journey to Zero Trust is to adopt stronger authentication methods instead of just a user id and password. The example code described above fully enables an enterprise to move to whatever stronger authentication method the enterprise chooses. That could be a multifactor authentication, fully passwordless with a FIDO2 key, or Microsoft Authenticator.

## Next steps

- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to determine your application permission approach to credential management.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- [Providing application identity credentials when there is no user](identity-non-user-applications.md) explains why the best Zero Trust client credentials practice for services (non-user applications) on Azure is Managed Identities for Azure Resources.
- [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) will help you to understand best practices for your application development lifecycle so that you can create secure applications that are [Zero Trust compliant](identity-zero-trust-compliance.md).
