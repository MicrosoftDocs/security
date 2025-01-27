---
title: Recommended SharePoint access policies
description: Describes the policies for Microsoft recommendations about how to secure SharePoint file access.
author: chrisda
ms.author: chrisda
manager: dansimp
ms.service: microsoft-365-zero-trust
ms.topic: conceptual
audience: Admin
f1.keywords:
  - NOCSH
ms.reviewer: martincoetzer
ms.custom:
  - it-pro
  - goldenconfig
ms.collection:
  - M365-identity-device-management
  - m365-security
  - m365solution-identitydevice
  - m365solution-scenario
  - zerotrust-solution
  - highpri
  - tier1
search.appverid: met150
ms.date: 01/23/2025
---

# Policy recommendations for securing SharePoint sites and files

This article describes how to implement the recommended Zero Trust identity and device access policies to protect SharePoint and OneDrive. This guidance builds on the [common identity and device access policies](zero-trust-identity-device-access-policies-common.md).

These recommendations are based on three different tiers of security and protection that can be applied based on the granularity of your needs: **starting point**, **enterprise**, and **specialized security**. You apply these policies based on the granularity of your needs. For more information, see [recommended security policies and configurations introduction](zero-trust-identity-device-access-policies-overview.md).

Also, you need to configure SharePoint sites with the right amount of protection, including appropriate permissions for enterprise and specialized security content.

## Updating common policies to include SharePoint and OneDrive

To protect files in SharePoint and OneDrive, the following diagram illustrates which policies to update from the common identity and device access policies.

:::image type="content" source="media/microsoft-365-policies-configurations/identity-access-rule-set-sharepoint.svg" alt-text="Diagram that shows the summary of policy updates for protecting the access to SharePoint" lightbox="media/microsoft-365-policies-configurations/identity-access-rule-set-sharepoint.svg":::

If you included SharePoint in the scope of the policies when you set them up, you only need to create the new policies. In Conditional Access policies, SharePoint includes OneDrive.

The new policies implement device protection for enterprise and specialized security content by applying specific access requirements to the specified SharePoint sites.

The following table lists the policies that you need to update or create for SharePoint. Each policy links to the associated configuration instructions in [Common identity and device access policies](zero-trust-identity-device-access-policies-common.md).

|Protection level|Policies|More information|
|---|---|---|
|**Starting point**|[Require MFA when sign-in risk is *medium* or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Include SharePoint in the assignment of cloud apps.|
||[Block clients that don't support modern authentication](zero-trust-identity-device-access-policies-common.md#block-clients-that-dont-support-multifactor-authentication)|Include SharePoint in the assignment of cloud apps.|
||[Apply APP data protection policies](zero-trust-identity-device-access-policies-common.md#app-protection-policies)|Be sure all recommended apps are included in the list of apps. Be sure to update the policy for each platform (iOS/iPadOS, Android, and Windows).|
||[Use app enforced restrictions in SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Add this new policy. This setting tells Microsoft Entra ID to use the settings specified in SharePoint. This policy applies to all users, but only affects access to sites included in SharePoint access policies.|
|**Enterprise**|[Require MFA when sign-in risk is *low*, *medium*, or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Include SharePoint in the assignments of cloud apps.|
||[Require compliant PCs *and* mobile devices](zero-trust-identity-device-access-policies-common.md#require-compliant-pcs-and-mobile-devices)|Include SharePoint in the list of cloud apps.|
||[SharePoint access control policy](#sharepoint-access-control-policies): Allow browser-only access to specific SharePoint sites from unmanaged devices.|This policy prevents editing and downloading of files. Use PowerShell to specify sites.|
|**Specialized security**|[*Always* require MFA](zero-trust-identity-device-access-policies-common.md#always-require-mfa)|Include SharePoint in the assignment of cloud apps.|
||[SharePoint access control policy](#use-app-enforced-restrictions-in-sharepoint): Block access to specific SharePoint sites from unmanaged devices.|Use PowerShell to specify sites.|

## Use app-enforced restrictions in SharePoint

If you implement access controls in SharePoint, Conditional Access policies are created in Microsoft Entra ID that enforce the policies you configure in SharePoint. By default, this policy applies to all users, but only affects access to the sites you specify using PowerShell when you create the access controls in SharePoint. The policy can also be scoped for specific users, groups, or sites.

To configure this policy, see [Block or limit access to a specific SharePoint site or OneDrive](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive).

## SharePoint access control policies

We recommend that you use device access controls to protect content in SharePoint sites that contain enterprise and specialized security. Create a policy that specifies the level of protection and the sites that receive the protection:

- **Enterprise sites**: Allow browser-only access. This setting prevents users from downloading, printing, or syncing files.
- **Specialized security sites**: Block access from unmanaged devices.

For more information, see [Block or limit access to a specific SharePoint site or OneDrive](/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive).

## How these policies work together

It's important to understand that SharePoint site permissions are typically based on business need for access to sites. Site owners manage these permissions, which can be highly dynamic. Using SharePoint device access policies ensures protection to these sites, regardless of whether users are assigned to a Microsoft Entra group associated with starting point, enterprise, or specialized security protection.

The following illustration provides an example of how SharePoint device access policies protect access to sites for a user.

:::image type="content" source="media/microsoft-365-policies-configurations/sharepoint-rules-scenario.svg" alt-text="Diagram that shows an example of how SharePoint device access policies protect sites." lightbox="media/microsoft-365-policies-configurations/sharepoint-rules-scenario.svg":::

James has starting point Conditional Access policies assigned, but he can get access to SharePoint sites with enterprise or specialized security protection:

- James is a member of a site with enterprise or specialized security protection. When he accesses the site using his PC, access is granted.
- James is a member of a site with enterprise protection. When he accesses the site using his unmanaged phone, he receives browser-only access due to the site's device access policy.
- James is a member of a site with specialized security protection. When he accesses the site using his unmanaged phone, access is blocked due to the site's device access policy. He can only access the site using his managed PC.

## Next step

:::image type="content" source="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Screenshot of the Step 4 - Policies for Microsoft 365 cloud apps." lightbox="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configure Conditional Access policies for:

- [Microsoft Teams](zero-trust-identity-device-access-policies-teams.md)
- [Exchange Online](zero-trust-identity-device-access-policies-exchange.md)
