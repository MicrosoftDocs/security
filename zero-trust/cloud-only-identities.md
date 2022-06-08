---
title: "Microsoft 365 cloud-only identity"
description: Describes how to create users and groups when your Microsoft 365 subscription is using cloud-only identity.
ms.date: 05/27/2022
ms.service: security
author: kelleyvice-msft
ms.author: kvice
ms.topic: conceptual
---

# Microsoft 365 cloud-only identity

*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*

If you have chosen the cloud-only identity model, you already have an Azure Active Directory (Azure AD) tenant for your Microsoft 365 subscription to store all of your users, groups, and contacts. After setting up protection for administrator accounts in [Step 2](protect-your-global-administrator-accounts.md) and user accounts in [Step 3](microsoft-365-secure-sign-in.md) of this solution, you are now ready to begin creating the new accounts and groups that your organization needs.

Here are the basic components of cloud-only identity.
 
:::image type="content" source="media/cloud-only-identity.png" alt-text="The basic components of cloud-only identity.":::

Users and their user accounts in organizations can be categorized in a number of ways. For example, some are employees and have a permanent status. Some are vendors, contractors, or partners that have a temporary status. Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration. For example:

- Tenant accounts represent users within your organization that you license for cloud services

- Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration

Take stock of the types of users in your organization. What are the groupings? For example, you can group users by high-level function or purpose to your organization.

Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.

You can use groups in Azure AD for several purposes that simplify management of your cloud environment. For example, with Azure AD groups, you can:

- Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.
- Add user accounts to specific groups dynamically based on user account attributes, such as department name.
- Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access policies.
- Provision permissions and levels of access for teams and SharePoint Online team sites.

## Next steps for cloud-only identity

- [Manage user accounts](/microsoft-365/enterprise/manage-microsoft-365-accounts?view=o365-worldwide)
- [Assign licenses to user accounts](/microsoft-365/enterprise/assign-licenses-to-user-accounts?view=o365-worldwide)
- [Manage groups and group membership](/microsoft-365/enterprise/manage-microsoft-365-groups?view=o365-worldwide)
- [Manage user account passwords](/microsoft-365/enterprise/manage-microsoft-365-passwords?view=o365-worldwide)
