---
title: Getting Started with Zero Trust Identity Integrations
description: Getting Started with Cloud Security Integrations
ms.date: 04/20/2021
ms.service: security
author: knicholasa
ms.author: nichola
ms.topic: conceptual
---

# Getting started with Zero Trust identity integrations

Knowing where to begin can be a challenge when integrating with Microsoft’s identity features and services. The modern threat landscape is complex, and there are many integration options to evaluate.

Microsoft identity publishes its own identity priorities based on the latest customer needs, security threats, and industry trends. In 2021, Microsoft Identity released an updated list of priorities, including:

:::image type="content" source="../media/diagram-identity-priorities.png" alt-text="List of priorities for Microsoft identity in 2021 including: trust in zero trust, secure access to all apps, go passwordless, choose and build secure-by-design apps, break collaboration boundaries" border="true":::

You can read more about these priorities in [the blog](https://www.microsoft.com/security/blog/2021/01/28/5-identity-priorities-for-2021-strengthening-security-for-the-hybrid-work-era-and-beyond/).

This overview explains the central features you can get started integrating with today. You can use this document as inspiration and a starting point before exploring other deeper identity integrations.

## List your app in the Azure AD App Gallery

Security solutions often require sensitive permissions related to users and applications in the customers tenant. Publishing your app in [the app gallery](https://www.microsoft.com/security/business/identity-access-management/integrated-apps-azure-ad) will increase customer trust. Customers will know that your application has been validated as compatible with Azure Active Directory, and you can become a [verified publisher](/azure/active-directory/develop/publisher-verification-overview) so that customers are certain you are the publisher of the app they are adding to their tenant. 

In addition, publishing in the app gallery will make it easy for IT admins to integrate the solution into their tenant with automated app registration. Manual registrations are a common cause of support issues with applications. Adding your app to the gallery will avoid these issues with your app.

## Integrate user provisioning

Managing identities and access for organizations with thousands of users is challenging. If your solution will be used by large organizations, synchronizing information about users and access between your application and Azure AD is essential. This allows you to effectively scale your identity management systems on both cloud-only and hybrid environments as customers increase their dependence on the cloud.

SCIM (System for Cross-Domain Identity Management) is an open standard for exchanging user identity information. You can use the SCIM user management API to automatically provision users and groups between your application and Azure AD.

Our tutorial on the subject, [develop a SCIM endpoint for user provisioning to apps from Azure AD](/azure/active-directory/app-provisioning/use-scim-to-provision-users-and-groups), describes how to build a SCIM endpoint and integrate with the Azure AD provisioning service. The SCIM specification provides a common user schema for provisioning. When used in conjunction with federation standards like SAML or OpenID Connect, SCIM gives administrators an end-to-end, standards-based solution for access management.

## Integrate with key security APIs

In our experience, many security ISVs have found these APIs to be particularly useful in improving their security solution and helping customers achieve Zero Trust.

### User and group APIs

When you integrate User Provisioning, you can keep your application up to date with changes in the tenant where your application resides. But if your application needs to make updates to the users and groups in the tenant, you can use the User and Group APIs through Microsoft Graph to write back to the Azure Active Directory tenant. You can read more about using the API in the [Microsoft Graph REST API v1.0 reference](/graph/api/overview) in the reference documentation for [/graph/api/user-getmembergroups](/graph/api/user-getmembergroups)

### Conditional Access API

[Conditional access](/azure/active-directory/conditional-access/overview) is a key part of Zero Trust because it helps to ensure the right user has the right access to the right resources. Enabling Conditional Access allows Azure Active Directory to make access decision based on computed risk and preconfigured policies.

ISVs can take advantage of conditional access by surfacing the option to apply conditional access policies when relevant to the customers. For example, if a user is especially risky, you can suggest the customer enable Conditional Access for that user through your UI, and programmatically enable it in Azure Active Directory.

:::image type="content" source="../media/diagram-access-control.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to set conditions for a conditional access policy based on the user activity." border="true" lightbox="../media/diagram-access-control.png":::

For more, check out the [configure conditional access policies using the Microsoft Graph API](https://github.com/Azure-Samples/azure-ad-conditional-access-apis/tree/main/01-configure/graphapi) sample on GitHub.

### Confirm compromise and risky user APIs

Sometimes ISVs may become aware of compromise that is outside of the scope of Azure Active Directory. For any security event, especially those including account compromise, Microsoft and the ISV can collaborate by sharing information from both parties. The [confirm compromise API](/graph/api/riskyusers-confirmcompromised) allows you to set a targeted user’s risk level to high. This lets Azure Active Directory respond appropriately, for example by requiring the user to reauthenticate or by restricting their access to sensitive data.

:::image type="content" source="../media/diagram-confirm-compromise.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to set user risk level to high." border="true" lightbox="../media/diagram-access-control.png":::

Going in the other direction, Azure AD continually evaluates user risk based on various signals and machine learning. The Risky User API provides programmatic access to all at-risk users in the app’s Azure Active Directory tenant. ISVs can make use of this API to ensure they are handling users appropriately to their current level of risk. [riskyUser resource type](/graph/api/resources/riskyuser).

:::image type="content" source="../media/diagram-risky-user.png" alt-text="Diagram showing a user using an application, which then calls Azure Active Directory to retrieve the user's risk level." border="true" lightbox="../media/diagram-access-control.png":::

## Next steps

- [Secure hybrid access integrations](secure-hybrid-access.md)

- [Become a Microsoft-compatible FIDO2 security key vendor](fido2-hardware-vendor.md)
