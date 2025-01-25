---
title: Recommended Teams access policies
description: Describes the recommended policies to secure Teams communication and file access.
author: MicrosoftHeidi
manager: dansimp
ms.service: microsoft-365-zero-trust
ms.topic: conceptual
audience: Admin
f1.keywords: 
  - NOCSH
ms.author: heidip
ms.date: 01/23/2025
ms.reviewer: anmorgan
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
---

# Policy recommendations for securing Teams chats, groups, and files

This article describes how to implement the recommended Zero Trust identity and device access policies to protect Microsoft Teams chats, groups, and content (for example, files and calendars). This guidance builds on the [common identity and device access policies](zero-trust-identity-device-access-policies-common.md), with additional information that's Teams-specific. Because Teams integrates with our other products, also see [Policy recommendations for securing SharePoint sites and files](zero-trust-identity-device-access-policies-sharepoint.md) and [Policy recommendations for securing email](zero-trust-identity-device-access-policies-exchange.md).

These recommendations are based on three different tiers of security and protection that can be applied based on the granularity of your needs: **starting point**, **enterprise**, and **specialized security**. You apply these policies based on the granularity of your needs. For more information, see [recommended security policies and configurations introduction](zero-trust-identity-device-access-policies-overview.md).

Specific recommendations for Teams are included in this article to cover authentication scenarios, including users outside the organization. Follow this guidance for a complete security experience.

## Getting started with Teams before other dependent services

You don't need to enable dependent services to get started with Microsoft Teams. These services will all "just work." However, you do need to be prepared to manage the following service-related elements:

- Exchange Online mailboxes
- Microsoft 365 Groups
- OneDrive
- SharePoint team sites
- Stream videos and Planner plans (if these services are enabled)

## Updating common policies to include Teams

To protect chats, groups, and content in Teams, the following diagram illustrates which policies to update from the common identity and device access policies. In each policy that requires an update, be sure to include Teams and the dependent services in the assignment of cloud apps.

:::image type="content" source="media/microsoft-365-policies-configurations/identity-access-rule-set-teams.svg" alt-text="Diagram that shows the summary of policy updates for the protection of access to Teams and its dependent services." lightbox="media/microsoft-365-policies-configurations/identity-access-rule-set-teams.svg":::

The dependent services that you need to include are described in the following list:

- Microsoft Teams
- SharePoint and OneDrive
- Exchange Online (mailboxes)
- Microsoft Stream (meeting recordings)
- Microsoft Planner (Planner tasks and plan data)

Review the policies listed in the following table and make the recommended additions for Microsoft Teams or confirm that these settings are already included. Each policy links to the associated configuration instructions in [Common identity and device access policies](zero-trust-identity-device-access-policies-common.md).

|Protection level|Policies|Further information for Teams implementation|
|---|---|---|
|**Starting point**|[Require multifactor authentication (MFA) when sign-in risk is *medium* or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Be sure Teams and dependent services are included in the list of apps. Teams has Guest Access and External Access rules to consider, which are described later in this article.|
||[Block clients that don't support modern authentication](zero-trust-identity-device-access-policies-common.md#block-clients-that-dont-support-multifactor-authentication)|Include Teams and dependent services in the assignment of cloud apps.|
||[High risk users must change password](zero-trust-identity-device-access-policies-common.md#high-risk-users-must-change-password)|Forces Teams users to change their password when signing in if high-risk activity is detected for their account. Be sure Teams and dependent services are included in the list of apps.|
||[Apply APP data protection policies](zero-trust-identity-device-access-policies-common.md#app-protection-policies)|Be sure Teams and dependent services are included in the list of apps. Update the policy for each platform (iOS/iPadOS, Android, and Windows).|
|**Enterprise**|[Require MFA when sign-in risk is *low*, *medium*, or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Teams has Guest Access and External Access rules to consider, which are described later in this article. Include Teams and dependent services in this policy.|
||[Define device compliance policies](zero-trust-identity-device-access-policies-common.md#create-device-compliance-policies)|Include Teams and dependent services in this policy.|
||[Require compliant PCs *and* mobile devices](zero-trust-identity-device-access-policies-common.md#require-compliant-pcs-and-mobile-devices)|Include Teams and dependent services in this policy.|
|**Specialized security**|[*Always* require MFA](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Include Teams and dependent services in this policy.|

## Teams dependent services architecture

For reference, the following diagram illustrates the services Teams relies on. For more information, see [Microsoft Teams and related productivity services in Microsoft 365 for IT architects](/microsoft-365/solutions/productivity-illustrations).

:::image type="content" source="media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="The diagram showing Teams dependencies on SharePoint, OneDrive, and Exchange Online." lightbox="media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## Guest and external access for Teams

Microsoft Teams defines the following access types for users outside the organization:

- **Guest access**: Uses a Microsoft Entra B2B account for each user that can be added as a member of a team. Guest access allows access to Teams resources and interaction with internal users in group conversations, chats, and meetings.

  For more information about guest access and how to implement it, see [Teams guest access](/microsoftteams/guest-access).

- **External access**: Users outside the organization who don't have Microsoft Entra B2B accounts. External access can include invitations and participation in calls, chats, and meetings, but doesn't include team membership or access to the resources of the team. External access is a way for Teams users in an external domain to find, call, chat with, and set up meetings in Teams with users in your organization.

  Teams administrators configure external access at the organization level. For more information, see [IT Admins - Manage external meetings and chat with people and organizations using Microsoft identities](/microsoftteams/trusted-organizations-external-meetings-chat).

External access users have less access and functionality than guest access users. For example, external access users can chat with your internal users with Teams but can't access team channels, files, or other resources.

Conditional Access policies apply only to guest access in Teams because there are corresponding Microsoft Entra B2B accounts. External access doesn't use Microsoft Entra B2B accounts and therefore doesn't use Conditional Access policies.

For recommended policies to allow access with a Microsoft Entra B2B account, see [Policies for allowing guest and external B2B account access](zero-trust-identity-device-access-policies-guest-access.md).

## Teams policies

Besides the previously described common policies, there are Teams-specific policies that you need to configure to manage specific features in Teams.

### Team and channel policies

Policies are available to control what users can and can't do in teams and channels in Teams. Although global teams are available, you're more likely to create smaller and more specific teams and channels to meet your business needs.

We recommend changing the default global policy or creating custom policies as described in: [Manage teams policies in Microsoft Teams](/microsoftteams/teams-policies).

### Messaging policies

You can also manage messaging (also known as chat) using the default global policy or custom policies. This approach helps users communicate in ways that are appropriate for your organization. For more information, see [Managing messaging policies in Teams](/microsoftteams/messaging-policies-in-teams).

### Meeting policies

Meetings allow small and large groups of people to formally get together and share relevant content. Setting the right organization policies for meetings is essential. For more information, see review [Manage meeting policies in Teams](/microsoftteams/settings-policies-reference#meetings).

### App permission policies

You can also use apps within Teams, such as in channels or in personal chats. Policies that define what apps can be use and where apps can be used are essential for a content-rich environment that's also secure.

For more information about app permission policies, see [Use app permission policies to control user access to apps](/microsoftteams/teams-app-permission-policies).

## Next steps

:::image type="content" source="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Screenshot of the policies for Microsoft 365 cloud apps." lightbox="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configure Conditional Access policies for:

- [Exchange Online](zero-trust-identity-device-access-policies-exchange.md)
- [SharePoint](zero-trust-identity-device-access-policies-sharepoint.md)
