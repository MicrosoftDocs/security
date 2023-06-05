---
title: Configuring group claims and app roles in tokens
description: Learn how to configure your apps with app role definitions and assign security groups to app roles to improve flexibility and control while increasing application zero trust security with least privilege.
ms.service: identity
author: janicericketts
ms.author: jricketts
ms.topic: conceptual
ms.date: 12/13/2022
ms.custom: template-concept
ms.collection:
  - zerotrust-dev
# Customer intent: As a developer, I want to learn how to configure my apps with app role definitions and assign security groups to app roles so that I can improve flexibility and control while increasing application security with least privilege.
---
# Configuring group claims and app roles in tokens

[Configuring group claims and app roles in tokens](configure-tokens-group-claims-app-roles.md) shows you how to configure your apps with app role definitions and assign security groups to app roles so that you can improve flexibility and control while increasing application security with least privilege.

Azure Active Directory (Azure AD) supports sending a user's assigned [security groups](/azure/active-directory/develop/active-directory-optional-claims), Azure AD directory roles, and distribution groups as claims in a token. You can use this approach to drive authorization in apps. However, Azure AD limits security group support in a token by the size of the token. If the user is a member of too many groups, there will be no security groups in the token.

In this article, you'll learn an alternative approach to getting user information in tokens using Azure AD security group support. Instead, you'll configure your apps with app role definitions and assign security groups to app roles. This [Zero Trust](overview.md) developer best practice will improve flexibility and control while [increasing application security with least privilege](/azure/active-directory/develop/secure-least-privileged-access).

You can [configure group claims](/azure/active-directory/develop/active-directory-optional-claims#configuring-groups-optional-claims) in tokens that you can use within your applications for authorization. Remember that group information in the token is current only when you receive the token. Group claims support two main patterns:

- Groups identified by their Azure AD object identifier (OID) attribute.
- Groups identified by the `sAMAccountName` or `GroupSID` attribute for Active Directory-synchronized groups and users.

Group membership can drive authorization decisions. For example, the following example shows some claims in a token. You can add group claims and roles to either ID or access tokens.

```
"aud": "e18c04b1-4868-4b93-93d1-8d71f17ab99b", 
"iss": "https://login.microsoftonline.com/833ced3d-cb2e-41de-92f1-29e2af035ddc/v2.0", 
"iat": 1669657224, "nbf": 1669657224, "exp": 1669661124, 
"groups": [ 
   "0760b6cf-170e-4a14-91b3-4b78e0739963", 
   "3b2b0c93-acd8-4208-8eba-7a48db1cd4c0" 
 ],
"oid": "cb7eda1b-d09a-40ae-b8bb-37836ebc6abd",
"sub": "3OBtLXUC2ZrN_ADLNjW9X4o0lcd61py7lgHw3Skh77s",
"tid": "833ced3d-cb2e-41ce-92f1-29e2af035ddc", 
"ver": "2.0", 
"wids": [ 
   "cf1c38e5-3621-4004-a7cb-879624dced7c", 
   "b79fbf4d-3ef9-4689-8143-76b194e85509" 
 ]
```

The `groups` claims array comprises the IDs of the groups to which this user is a member. The `wids` array comprises the IDs of the Azure AD roles assigned to this user. Here, `cf1c38e5-3621-4004-a7cb-879624dced7c` shows that this user's assigned roles include Application Developer and standard member as `3b2b0c93-acd8-4208-8eba-7a48db1cd4c0` indicates.

Your app can make authorization decisions based on the presence or absence of these claims and their values. See [Azure AD built-in roles](/azure/active-directory/roles/permissions-reference) for a list of values for the `wids` claim.

To add the `groups` and `wids` claims to your tokens, select **All groups** as shown in the following example of the **App registrations** | **Token configuration** | **Optional claims** | **Edit groups claim** screen.

:::image type="content" source="../media/develop/configure-tokens-group-claims-app-roles/screenshot-add-groups-claim-all-groups-inline.png" alt-text="Screenshot of Edit group claims screen shows selected group types: Groups assigned to the application." lightbox="../media/develop/configure-tokens-group-claims-app-roles/screenshot-add-groups-claim-all-groups-expanded.png":::

## Group overages

When you request all groups in your token as shown in the above example, you can't rely on the token having the `groups` claim in your token. There are size limits on tokens and on `groups` claims so that they don't become too large. When the user is a member of too many groups, your app will need to get the user's group membership from Microsoft Graph. The limits for groups in a `groups` claim are:

- 200 groups for JWT tokens.
- 150 groups for SAML tokens.
- Six groups when using the implicit flow (for example, using ASP.NET core that gets ID tokens through the implicit flow part of a hybrid flow).
  - Implicit flow is no longer recommended for single page web apps.
  - Implicit flow can be used in web apps for the ID token only, never the access token, in an OAuth2 hybrid flow.

If you're using OpenID Connect or OAuth2, you can have up to 200 groups in your token. If you're using SAML, you can have only 150 groups because SAML tokens are bigger than OAuth2 and OpenID Connect tokens. If you're using the implicit flow, the limit is six because those responses show up in the URL. In all of these cases, instead of having a `groups` claim, you'll see an indication (known as a group overage) that tells you that the user is a member of too many groups to fit in your token.

In the following token example, for an OpenID connect, or OAuth2, JSON web token (JWT), there won't be a `groups` claim if the user is a member of too many groups. Instead, there will be a `_claim_names` claim that contains a `groups` member of the array.

:::image type="content" source="../media/develop/configure-tokens-group-claims-app-roles/screenshot-token-group-membership-azure-ad-graph-inline.png" alt-text="Screenshot of example token shows query of Azure AD Graph." lightbox="../media/develop/configure-tokens-group-claims-app-roles/screenshot-token-group-membership-azure-ad-graph-expanded.png":::

In the above token example, you see that the `groups` claim is supposed to be mapped to `src1`. In theory, you'd then look for the `_claim_sources` claim then find the `src1` member. From there, you'd find the Graph query that you'd use to get the group membership. However, there's a problem with what you see in the example Graph query. It goes to Azure AD Graph (which Microsoft is deprecating), so don't use it.

Implicit flow overage indication is done with a `hasgroups` claim instead of the `groups` claim.

To ensure proper authorization using group membership, have your app check for the `groups` claim. If present, use that claim to determine the user's group membership. If there's no `groups` claim, check for the existence of a `hasgroups` claim or a `_claim_names` claim with a `groups` member of the array. If either of these claims are present, the user is a member of too many groups for the token. In this case, your app must use Microsoft Graph to determine the group membership for the user. See [List a user's memberships (direct and transitive)](/graph/api/user-list-transitivememberof) to find all the groups, both direct and transitive, of which the user is a member.

If your application requires real time group membership information, use Microsoft Graph to determine group membership. Remember that the information in the token that you receive is up to date only at the time you call Microsoft Graph.

See the following example of the **App registrations** | **Token configuration** | **Optional claims** | **Edit groups claim** screen. One way to avoid hitting a group overage claim is to select **Groups assigned to the application** on the **Edit groups claim** screen instead of **All groups**.

:::image type="content" source="../media/develop/configure-tokens-group-claims-app-roles/screenshot-add-groups-claim-assigned-to-app-inline.png" alt-text="Screenshot of Edit group claims screen shows selected group types: Security groups, Directory roles, and All groups." lightbox="../media/develop/configure-tokens-group-claims-app-roles/screenshot-add-groups-claim-assigned-to-app-expanded.png":::

When you select **Groups assigned to the application**, a group is included in the `groups` claim if the following conditions are true:

- the group is [assigned to the Enterprise App](/azure/active-directory/manage-apps/assign-user-or-group-access-portal?pivots=portal)
- the user is a direct member of the group

As of this article's publication, the **Groups assigned to the application** option doesn't support indirect membership. Group assignment requires at least a P1 level license. A free tenant can't assign groups to an application.

## Groups and app roles

Another way to avoid the group overage problem is for the app to define app roles that allow users and groups as member types. As shown in the following example of the **App registrations** \| **App roles** \| **Create app role** screen, select **Users/Groups** for **Allowed member types**.

:::image type="content" source="../media/develop/configure-tokens-group-claims-app-roles/screenshot-create-app-role-allow-users-groups-inline.png" alt-text="Screenshot of Create app role screen shows Allowed member types: Users/Groups." lightbox="../media/develop/configure-tokens-group-claims-app-roles/screenshot-create-app-role-allow-users-groups-expanded.png":::

Having [created the app role in the app's registration](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps), IT Pros can [assign users and groups to the role](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps#assign-users-and-groups-to-roles). Your app will get a `roles` claim in your token (ID token for app, access token for APIs) with all the signed-in user's assigned roles as shown in the following token example.

```
"aud": "acaf6ce9-81f0-462a-a93d-a314070738d3",
"iss": "https://login.microsoftonline.com/833ced3d-cb2e-41de-92f1-29e2af035ddc/v2.0",
"iat": 1670826509, "nbf": 1670826509, "exp": 1670830409,
"name": "Kyle Marsh",
"oid": "cb7eda1b-d09a-419e-b8bb-37836ebc6abd",
"preferred_username": "kylemar@idfordevs.dev",
"roles": [
 "Approver",
 "Reviewer" 
],
"sub": "dx-4lf-0loB3c3uVrULnZ2VTLuRRWYff0q7-QlIfYU4",
"tid": "833ced3d-cb3e-41de-92f1-29e2af035ddc",
```

Remember to have your application handle the following conditions:

- absence of `roles` claim
- user hasn't been assigned to any role
- multiple values in the `roles` claim when the user has multiple assigned roles

When you create app roles that allow user and groups as members, always define a baseline user role with no elevated authorization roles. When an Enterprise App configuration requires assignment, only users with direct assignment to an application or membership in a group assigned to the app can use the app.

If your app has defined app roles that allow users and groups as members then, when a user or group is assigned to the app, one of the defined app roles must be part of the user or group's assignment to the app. If your app has only defined elevated roles (such as `admin`) for the app, then all users and groups would  be assigned the admin role. When you define a base role (such as `user`), users and groups assigned to the app can be assigned the base user role.

In addition to avoiding group overage claims, another advantage of using roles isn't needing to map between a group ID or name and what it means in your application. For example, your code can look for the admin role claim instead of iterating through groups in the `groups` claims and deciding which group IDs should be allowed the admin functionality.

## Verifying and using roles in your code

When you define app roles for your app, it is your responsibility to implement authorization logic for those roles. See [Implement role-based access control in applications](/azure/active-directory/develop/howto-implement-rbac-for-apps) to learn how you can implement authorization logic in your apps.

## Next steps

- [Customizing tokens](zero-trust-token-customization.md) describes the information that you can receive in Azure AD tokens and how to customize tokens to improve flexibility and control while increasing application zero trust security with least privilege.
- [Configure group claims for applications by using Azure Active Directory](/azure/active-directory/hybrid/how-to-connect-fed-group-claims) shows how Azure Active Directory (Azure AD) can provide a user's group membership information in tokens for use within applications.
- [Security best practices for application properties](/azure/active-directory/develop/security-best-practices-for-app-registration) describes redirect URI, access tokens (used for implicit flows), certificates and secrets, application ID URI, and application ownership.
- [Microsoft identity platform scopes, permissions, & consent](/azure/active-directory/develop/v2-permissions-and-consent) explains the foundational concepts of access and authorization to help you build more secure and trustworthy applications.
- Use [Zero Trust identity and access management development best practices](identity-iam-development-best-practices.md) in your application development lifecycle to create secure applications.
