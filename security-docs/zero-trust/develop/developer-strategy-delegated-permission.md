---
title: Developing delegated permissions strategy
description: As a developer, implement the best approach for managing permissions in your application and develop using Zero Trust.
author: janicericketts
ms.author: jricketts
ms.service: identity
ms.topic: conceptual
ms.date: 08/19/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to implement the best approach for managing permissions in my application and develop using Zero Trust.
---
# Developing delegated permissions strategy

This article will help you, as a developer, to implement the best approach for managing permissions in your application and [develop using Zero Trust principles](overview.md). As described in [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md), *delegated permissions* are used with delegated access to allow an application to act on behalf of a user, accessing only what the user can access. *Application permissions* are used with direct access to allow an application to access any data with which the permission is associated. Only administrators and owners of [service principals](/azure/active-directory/develop/active-directory-how-applications-are-added#what-are-service-principals-and-where-do-they-come-from) can consent to application permissions.

The permission and consent models refer primarily to an application. The permission and consent process has no control over what a user can do. It controls what actions the application is allowed to perform.

Reference the following Venn diagram. With delegated permissions, there's an intersection between what the user is allowed to do and what the application is allowed to do. That intersection is the effective permission by which the application is bound. Anytime you use a delegated permission, it's bounded by the effective permissions.

:::image type="complex" source="../media/develop/developer-strategy-delegated-permission/diagram-effective-permissions-inline.png" alt-text="Venn diagram shows effective permissions as intersection of app permissions and user capabilities." lightbox="../media/develop/developer-strategy-delegated-permission/diagram-effective-permissions-expanded.png":::
   "Venn diagram description: Left circle text: Apps are granted consent for the app's range of operation. Right circle text: Users have permissions for operations managed by their organization. Intersection of circles text: Effective permissions: intersection of app permissions and user capabilities."
:::image-end:::

For example, your application that has users in front of the app gets permission to update every user's profile in the tenant. That doesn't mean that anyone running your application can update anyone else's profile. If the admin decides to grant your application `User.ReadWrite.All`, then they believe that your application is doing the right things when updating any users profile. Your app might log the changes and properly safeguard the information. The admin makes a value judgment about the application, not about the user.

## Least privilege approach

APIs can be complex. Simple APIs may not have many operations. Complex APIs like Microsoft Graph encapsulate many requests that an application may want to use. Just because the application has the right to read doesn't mean it should have the right to update. For example, Microsoft Graph has thousands of APIs. Just because you have permission to read the user's profile, there's no reason why you should also have permission to delete all their OneDrive files.

As a developer, you should:

- know which APIs the app calls.
- understand the API documentation and what permissions the API requires.
- use the least possible permission to accomplish your tasks.

APIs often provide access to organization data stores and attract the attention of attackers who want to access that data.

Evaluate the permissions you request to ensure that you seek the absolute least privileged set to get the job done. Avoid requesting higher privilege permissions; instead, carefully work through the large number of permissions that APIs like Microsoft Graph provide. Locate and use the minimum permissions to address your needs. If you won't write code to update the user's profile, you won't request it for your application. If you only access users and groups, you won't request access to other information in the directory. You won't request permission to manage user email if you won't write code that accesses user email.

In Zero Trust application development:

- Define your application's intention and what it needs.
- Ensure that bad actors can't compromise and use your app in a way that you didn't intend.
- Make requests for approval in which you define your requirements (for example, read the user's mail).

## User and tenant administrator roles in permission and consent

People who can approve of your requests fall into two categories: admins who can always consent to permission requests and regular users who aren't admins. However, the tenant admins have the final say in their tenant regarding which permissions require admin consent and to which permissions a user can consent.

When an API designer requires admin consent for a permission, that permission will always require admin consent; a tenant admin can't overrule that and require only user consent.

When an API designer defines permissions that require user consent, user consent suggestions by the API designer can be overruled by the tenant admin. The tenant admins can do that with a "big switch" in the tenant: everything requires admin consent. They can overrule user consent in a more granular way with [permission and consent management](/azure/active-directory/manage-apps/configure-user-consent?tabs=azure-portal). For example, they may allow users to consent to user consent requests from [verified publishers](developer-strategy-authorization-best-practices.md#becoming-a-verified-publisher) but not from other publishers. In another example, they may allow `User.Read` to sign in the user and read their profile but require admin consent to apps that ask permission to mail or to files.

API designers make their suggestions but tenant admins have the final say. Therefore, as a developer, you won't always know when your app requires admin consent. It's nice to plan and design around that but remember, when you make a token request, it could be denied for any reason. In your code, you need to gracefully handle not getting a token because tenant admins in which your customers or users are running your application decide when permissions require admin consent.

## Example using JavaScript MSAL

For the authentication in this example, you'll use our JavaScript Microsoft Authentication Library (MSAL) to sign in the user in a single page application (SPA) where all the app logic executes from the browser.

From the related [Quickstart article](/azure/active-directory/develop/single-page-app-quickstart?pivots=devlang-javascript), you can [download](/azure/active-directory/develop/single-page-app-quickstart?pivots=devlang-javascript#step-2-download-the-project) and run a code sample. It demonstrates how a JavaScript single-page application (SPA) can sign in users and call Microsoft Graph using the authorization code flow with Proof Key for Code Exchange (PKCE). The code sample shows how to get an access token to call the Microsoft Graph API or any web API.

As shown in the example code below, you'll instantiate a public client because an application that runs entirely in the browser must be a public client. The user can get their hands on the internals of your application when the code is in the browser.

```javascript
// Create the main myMSALObj instance
// configuration parameters are located at authConfig.js
const myMSALObj = new msal.PublicClientApplication(msalConfig);
```

Then you'll use our MSAL library. In MSAL JavaScript, there's a specific API to sign in. There are two APIs that utilize specific capabilities within the browser. One is to sign in with a pop-up experience; the other one is to sign in with a browser redirect experience.

As shown in the code example below, the sign-in pop-up handles the authentication that the user needs to perform by calling the `signIn` function.

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

Your app can get information about the user, such as their display name or user ID. Next, your app needs authorization to read the full profile of the user from Microsoft Graph by following a pattern that you'll use throughout our MSAL libraries.

As shown in the example code below, your app attempts to get the authorization by calling `AcquireTokenSilent`. If Microsoft Entra ID can issue the token without interacting with the user, then `AcquireTokenSilent` will return the token that your app needs to access Microsoft Graph on behalf of the user.

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

However, often Microsoft Entra ID can't issue the token without interacting with the user (for example, the user changed their password or  they haven't granted consent). Therefore, `AcquireTokenSilent` will send an error back to the application it requires user interaction. When you're your app receives the error, you'll fall back to call `AcquireTokenPopup`.

At that point, Microsoft Entra ID will have a conversation with the user so they can authenticate the user and authorize your app to act on the user's behalf (for example, do an MFA, provide their password, grant consent). Then your app will get the token needed to move forward.

A primary step in an enterprise's journey to Zero Trust is to adopt stronger authentication methods instead of just a user ID and password. The example code described above fully enables an enterprise to move to the stronger authentication method that the enterprise chooses. For example, multifactor authentication, fully passwordless with a FIDO2 key, Microsoft Authenticator.

## Next steps

- [Acquiring authorization to access resources](acquire-application-authorization-to-access-resources.md) helps you to understand how to best ensure Zero Trust when acquiring resource access permissions for your application.
- [Developing application permissions strategy](developer-strategy-application-permissions.md) helps you to decide upon your application permissions approach to credential management.
- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Microsoft Entra tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Calling an API from another API](api-calls-api.md) helps you to ensure Zero Trust when you have one API that needs to call another API and securely develop your application when it's working on behalf of a user.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
