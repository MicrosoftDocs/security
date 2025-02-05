---
title: Secure email recommended policies
description: Describes the policies for Microsoft recommendations about how to apply email policies and configurations.
author: chrisda
ms.author: chrisda
manager: deniseb
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
  - remotework
  - m365solution-identitydevice
  - m365solution-scenario
  - zerotrust-solution
  - highpri
  - tier1
search.appverid: met150
ms.date: 02/05/2025
---

# Policy recommendations for securing email

This article describes how to protect cloud email and email clients by implementing the recommended Zero Trust identity and device access policies. This protection requires email clients and devices that support modern authentication and Conditional Access. This guidance builds on the [Common identity and device access policies](zero-trust-identity-device-access-policies-common.md) and also includes additional recommendations.

These recommendations are based on three different tiers of security and protection that can be applied based on the granularity of your needs: **starting point**, **enterprise**, and **specialized security**. You can learn more about these security tiers and the recommended client operating systems in the [recommended security policies and configurations introduction](zero-trust-identity-device-access-policies-overview.md).

These recommendations require using modern email clients on mobile devices. Outlook for iOS and Android supports the best features of Microsoft 365. The security capabilities in Outlook for iOS and Android support mobile use and work together with other Microsoft cloud security features. For more information, see [Outlook for iOS and Android FAQ](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## Update common policies to include email

To protect email, the following diagram illustrates which policies to update from the common identity and device access policies.

:::image type="content" source="media/microsoft-365-policies-configurations/identity-access-rule-set-mail.svg" alt-text="Diagram that shows the summary of policy updates for protecting access to Microsoft Exchange." lightbox="media/microsoft-365-policies-configurations/identity-access-rule-set-mail.svg":::

Notice the addition of a new policy for Exchange Online to block ActiveSync clients. This policy forces the use of Outlook for iOS and Android on mobile devices.

If you included Exchange Online and Outlook in the scope of the policies when you set them up, you only need to create the new policy to block ActiveSync clients. Review the policies listed in the following table and make the recommended additions for email or confirm that these settings are already included. Each policy links to the associated configuration instructions in [Common identity and device access policies](zero-trust-identity-device-access-policies-common.md).

|Protection level|Policies|More information|
|---|---|---|
|**Starting point**|[Require MFA when sign-in risk is *medium* or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Include Exchange Online in the assignment of cloud apps.|
||[Block clients that don't support modern authentication](zero-trust-identity-device-access-policies-common.md#block-clients-that-dont-support-multifactor-authentication)|Include Exchange Online in the assignment of cloud apps.|
||[Apply APP data protection policies](zero-trust-identity-device-access-policies-common.md#app-protection-policies)|Be sure Outlook is included in the list of apps. Be sure to update the policy for each platform (iOS, Android, Windows).|
||[Require approved apps or app protection policies](zero-trust-identity-device-access-policies-common.md#require-approved-apps-or-app-protection-policies)|Include Exchange Online in the list of cloud apps.|
||[Verify automatic email forwarding to external recipients is disabled](#verify-automatic-email-forwarding-to-external-recipients-is-disabled)|By default, the default outbound spam policy blocks automatic external email forwarding, but admins can change the setting.|
||[Block Exchange ActiveSync clients](#block-exchange-activesync-clients)|Add this new policy.|
|**Enterprise**|[Require MFA when sign-in risk is *low*, *medium*, or *high*](zero-trust-identity-device-access-policies-common.md#require-mfa-based-on-sign-in-risk)|Include Exchange Online in the assignment of cloud apps.|
||[Require compliant PCs *and* mobile devices](zero-trust-identity-device-access-policies-common.md#require-compliant-pcs-and-mobile-devices)|Include Exchange Online in the list of cloud apps.|
|**Specialized security**|[*Always* require MFA](zero-trust-identity-device-access-policies-common.md#always-require-mfa)|Include Exchange Online in the assignment of cloud apps.|

## Verify automatic email forwarding to external recipients is disabled

By default, outbound spam policies in Exchange Online Protection (EOP) block automatic email forwarding to external recipients by [Inbox rules](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) or by [mailbox forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (also known as *SMTP forwarding*). For more information, see [Control automatic external email forwarding in Microsoft 365](/defender-office-365/outbound-spam-policies-external-email-forwarding).

In all outbound spam policies, verify the value of the **Automatic forwarding rules** setting is **Automatic - System-controlled** or **Off - Forwarding is disabled** (both values block automatic external email forwarding). A default policy applies to all users, and admins can create custom policies that apply to specific groups of users. For more information, see [Configure outbound spam policies in EOP](/defender-office-365/outbound-spam-policies-configure).

## Block Exchange ActiveSync clients

Exchange ActiveSync synchronizes email and calendar data on desktop and mobile devices.

For mobile devices, the following clients are blocked based on the Conditional Access policy created in [Require approved apps or app protection policies](zero-trust-identity-device-access-policies-common.md#require-approved-apps-or-app-protection-policies):

- ActiveSync clients that use basic authentication.
- ActiveSync clients that support modern authentication, but not Intune app protection policies.
- Devices that support Intune app protection policies but aren't defined in the policy.

To block ActiveSync connections that use basic authentication on other types of devices (for example, PCs), follow the steps in [Block Exchange ActiveSync on all devices](/entra/identity/conditional-access/policy-all-users-approved-app-or-app-protection#block-exchange-activesync-on-all-devices).

## Limit access to email attachments in Outlook on the web and the new Outlook for Windows

You can restrict users on unmanaged devices from downloading email attachments in Outlook on the web (formerly known as Outlook Web App or OWA) and in the new Outlook for Windows. Users can view and edit these files using Office Online without leaking and storing the files on the device. You can also block users from even seeing attachments in Outlook on the web and the new Outlook for Windows on unmanaged devices.

You enforce these restrictions using Outlook on the web mailbox policies in Exchange Online. Every Microsoft 365 organization with Exchange Online mailboxes has a built-in Outlook on the web mailbox policy named OwaMailboxPolicy-Default. By default, this policy is applied to all users. Admins can also [create custom policies](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy) that apply to specific groups of users.

Here are the steps to limit access to email attachments:

1. [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. To see the available Outlook on the web mailbox policies, run the following command:

   ```powershell
   Get-OwaMailboxPolicy | Format-Table Name,ConditionalAccessPolicy
   ```

3. To allow viewing but not downloading attachments, replace \<PolicyName\> with the name of the affected policy, and then run the following command:

   ```powershell
   Set-OwaMailboxPolicy -Identity "<PolicyName>" -ConditionalAccessPolicy ReadOnly
   ```

   For example:

   ```powershell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -ConditionalAccessPolicy ReadOnly
   ```

4. To block viewing attachments, replace \<PolicyName\> with the name of the affected policy, and then run the following command:

   ```powershell
   Set-OwaMailboxPolicy -Identity "<PolicyName>" -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

   For example:

   ```powershell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. On the **Conditional Access \| Overview** page in the Microsoft Entra admin center at <https://entra.microsoft.com/#view/Microsoft_AAD_ConditionalAccess/ConditionalAccessBlade/~/Overview>, [create a new Conditional Access policy](/entra/identity/conditional-access/concept-conditional-access-policies) with the following settings:

   - **Assignments** section:
     - **Users**: Select appropriate users and groups to include and exclude on the **Include** and **Exclude** tabs.
     - **Target resources**: **Select what this policy applies to** \> **Resources (formerly cloud apps)** \> **Include** tab \> **Select resources** \> **Select** \> find and select **Office 365 Exchange Online**.

   - **Access controls** section: **Session** \> select **Use app enforced restrictions**.

   - **Enable policy** section: Select **On**.

## Require Outlook for iOS and Android on mobile devices

To require Outlook for iOS and Android for access to company data, you need a Conditional Access policy that targets those potential users.

Follow the steps to configure this policy in [Manage messaging collaboration access by using Outlook for iOS and Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## Set up message encryption

With Microsoft Purview Message Encryption, which uses protection features in Azure Information Protection, your organization can easily share protected email with anyone on any device. Users can send and receive protected messages with other organizations that use Microsoft 365, Outlook.com, Gmail, and other email services.

For more information, see [Set up Message Encryption](/purview/set-up-new-message-encryption-capabilities).

## Next steps

:::image type="content" source="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Screenshot of the policies for Microsoft 365 cloud apps." lightbox="media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Configure Conditional Access policies for:

- [Microsoft Teams](zero-trust-identity-device-access-policies-teams.md)
- [SharePoint](zero-trust-identity-device-access-policies-sharepoint.md)
