---
title: Customizing tokens
description: Learn about the information that you can receive in Microsoft Entra tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 12/13/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn about the information that I can receive in Microsoft Entra tokens and how I can customize tokens so that I can improve flexibility and control while increasing application security with least privilege.
---
# Customizing tokens

As a developer, your primary interaction with Microsoft Entra ID is in requesting a token to identify the user. You'll also request a token to get authorization to call a web API. The web API token determines what that API can do when it services a particular request. In this article, you'll learn about the information that you can receive in tokens and how you can customize tokens. These [Zero Trust](overview.md) developer best practices will improve flexibility and control while [increasing application security with least privilege](/azure/active-directory/develop/secure-least-privileged-access).

Your reasons for customizing your application tokens depend on the process you're using to drive more granular authorization in your applications and APIs. For example, you may have different user roles, access levels, and functionalities in your app that rely on information from tokens.

The Microsoft Graph API provides a robust set of directory information and data across Microsoft 365. You can develop a fine-grained and rich authorization system by building on the data in Microsoft Graph. For example, you can access information from the user's group membership, detailed profile data, SharePoint, and Outlook to use in your authorization decisions. You can also include authorization data in the token from Microsoft Entra ID.

## Application-level authorization

It's possible for IT Pros to add app-level authorization without customizing the token nor having the developer add any code.

IT Pros can prevent tokens from being issued to any app in the tenant by using the [user assignment required](/azure/active-directory/manage-apps/assign-user-or-group-access-portal) flag to ensure that only a set of users are able to sign in to the application. Without this flag, all users in a tenant can access the application. With this flag, only assigned users and groups can access the application. When an assigned user accesses the app, the app receives a token. If the user doesn't have an assignment, the app won't receive a token. Remember to always gracefully handle token requests that don't receive tokens.

## Token customization methods

There are two ways to customize tokens: optional claims and claims mapping.

### Optional claims

[Optional claims](/azure/active-directory/develop/active-directory-optional-claims) specify which claims you want Microsoft Entra ID to send to your application in tokens. You can use optional claims to:

- Select more claims to include in your application tokens.
- Change the behavior of claims that the Microsoft identity platform returns in tokens.
- Add and access custom claims for your application.

Optional claims hang off of the application registration object with a defined schema. They apply to the application no matter where it was running. When you're writing a multi-tenant application, optional claims work well because they're consistent across every tenant in Microsoft Entra ID. For example, an IP address isn't tenant-specific whereas an application has an IP address.

By default, guest users in a tenant can also sign in to your app. If you want to block guest users, [opt-in to the optional claim](/azure/active-directory/develop/active-directory-optional-claims) (acct). If it's 1, then the user has a guest classification. If you want to block guests, then block tokens with acct==1.

### Claims mapping

In Microsoft Entra ID, policy objects represent sets of rules on individual applications or on all applications in an organization. A [claims mapping policy](/azure/active-directory/develop/reference-claims-mapping-policy-type) modifies the claims that Microsoft Entra ID issues in tokens for specific applications.

You'll use claims mapping for tenant-specific information that has no schema (for example, EmployeeID, DivisionName). Claims mapping applies at the service principal level that the tenant admin controls. Claims mapping corresponds to the enterprise app or the service principal for that application. Each tenant can have its own claims mapping.

If you're developing a line of business application, you can look specifically at what your tenant does (what specific claims your tenant has available that you can use in your token). For example, if an organization has a user's division name property (not a standard field in Microsoft Entra ID) in their on-premises Active Directory, you can use [Microsoft Entra Connect](/azure/active-directory/hybrid/how-to-connect-sync-feature-directory-extensions) to sync it to Microsoft Entra ID.

You can use one of the standard extension attributes to contain that information. You can define your token with a division name claim that you can compose from the corresponding extension (even if it won't apply across every tenant). For example, an organization puts their division name in extension attribute 13.

With claims mapping, you can make it work for another tenant that puts their division name in attribute seven.

## Planning token customization

Which token you customize depends on your type of application: client application or API. There's no difference in what you can do to customize your token. What you can put in the token is the same for each of them. Which token you choose to customize depends upon which token your app will consume.

### Customizing ID tokens

If you're developing a client application, you customize the [ID token](/azure/active-directory/develop/id-tokens) because it's the token that you request to identify the user. A token belongs to your app when the audience claim (`aud`) in the token matches the client ID of your application. For a client application that calls APIs, but doesn't implement them, make sure you only customize your app's ID token.

The Azure portal and Microsoft Graph API allow you to customize the access token for your app as well, but those customizations have no effect. You can't customize an access token for an API that you don't own. Remember, your app must not attempt to decode or inspect an access token that your client app receives as authorization to call an API.

### Customizing access tokens

If you're developing an API, you customize the [access token](/azure/active-directory/develop/access-tokens) because your API will receive access tokens as part of the client's call to your API.

Client applications always customize the ID token that they receive to identity the user. APIs customize the access tokens that the API will receive as part of the call to the API.

## Groups and app roles

One of the most common authorization techniques is to base access on a user's group membership or assigned roles. [Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.

## Next steps

- [B2B collaboration user claims mapping](/azure/active-directory/external-identities/claims-mapping) describes Microsoft Entra ID support for customizing the claims that are issued in the SAML token for B2B collaboration users.
- [Customize app SAML token claims](/azure/active-directory/develop/active-directory-saml-claims-customization) when a user authenticates to an application through the Microsoft identity platform using the SAML 2.0 protocol.
- [API Protection](protect-api.md) describes best practices for protecting your API through registration, defining permissions and consent, and enforcing access to achieve your Zero Trust goals.
- [Authorization best practices](developer-strategy-authorization-best-practices.md) helps you to implement the best authorization, permission, and consent models for your applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
