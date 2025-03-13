---
title: Common Zero Trust identity and device access policies - Microsoft 365 for enterprise
description: Describes the recommended common Zero Trust identity and device access policies and configurations.
ms.author: joflore
author: MicrosoftGuyJFlo

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
  - tier2
search.appverid: met150
ms.date: 03/10/2025
---

# Common security policies for Microsoft 365 organizations

Organizations have a lot to worry about when deploying Microsoft 365 for their organization. The Conditional Access, app protection, and device compliance policies referenced in this article are based on Microsoft's recommendations and the three guiding principles of [Zero Trust](zero-trust-overview.md):

- Verify explicitly
- Use least privilege
- Assume breach

Organizations can take these policies as is or customize them to fit their needs. If possible, test your policies in a nonproduction environment before you roll them out to your production users. Testing is critical to identify and communicate any possible effects to your users.

We group these policies into three protection levels based on where you are on your deployment journey:

- **Starting point**: Basic controls that introduce multifactor authentication, secure password changes, and Intune app protection policies for mobile devices.
- **Enterprise**: Enhanced controls that introduce device compliance.
- **Specialized security**: Policies that require multifactor authentication every time for specific data sets or users.

The following diagram shows the protection levels that each policy applies to and what types of devices the policies apply to:

:::image type="content" source="media/microsoft-365-policies-configurations/identity-device-access-policies-by-plan.svg" alt-text="A diagram showing common identity and device policies that support Zero Trust principles." lightbox="media/microsoft-365-policies-configurations/identity-device-access-policies-by-plan.svg":::

You can download this diagram as a [PDF](https://download.microsoft.com/download/e/d/0/ed03381c-16ce-453e-9c89-c13967819cea/zero-trust-identity-and-device-access-policies.pdf) file.

> [!TIP]
> We recommend requiring multifactor authentication (MFA) for users before enrolling devices in Intune to ensure they are in possession of the device. MFA is on by default due to [security defaults](/entra/fundamentals/security-defaults#enforced-security-policies), or you can use [Conditional Access policies to require MFA for all users](/entra/identity/conditional-access/policy-all-users-mfa-strength).
>
> Devices must be enrolled in Intune before you can enforce device compliance policies.

## Prerequisites

### Permissions

The following permissions in Microsoft Entra are required:

- **Manage Conditional Access policies**: The [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) role.
- **Manage app protection and device compliance policies**: The [Intune Administrator](/entra/identity/role-based-access-control/permissions-reference#intune-administrator) role.
- **View configurations only**: The [Security Reader](/entra/identity/role-based-access-control/permissions-reference#security-reader) role.

For more information about roles and permissions in Microsoft Entra, see [Overview of role-based access control in Microsoft Entra ID](/entra/identity/role-based-access-control/custom-overview).

### User registration

Ensure that users register for MFA before you require it. If your licenses include Microsoft Entra ID P2, you can use the [MFA registration policy within Microsoft Entra ID Protection](/entra/id-protection/howto-identity-protection-configure-mfa-policy) to require users to register. We provide [communication templates](https://aka.ms/mfatemplates) that you can download and customize to promote user registration.

### Groups

All Microsoft Entra groups that you use as part of these recommendations must be Microsoft 365 Groups, **not** security groups. This requirement is important for the deployment of sensitivity labels to secure documents in Microsoft Teams and SharePoint. For more information, see [Learn about groups and access rights in Microsoft Entra ID](/entra/fundamentals/concept-learn-about-groups#group-types).

### Assigning policies

You can assign Conditional Access policies to users, groups, and administrator roles. You can assign Intune app protection and device compliance policies to *groups only*. Before you configure your policies, identify who should be included and excluded. Typically, starting point protection level policies apply to everyone in the organization.

The following table describes example group assignments and exclusions for MFA after users complete [user registration](#user-registration):

|&nbsp;|Microsoft Entra Conditional Access policy|Include|Exclude|
|---|---|:---:|---|
|**Starting point**|Require multifactor authentication for **Medium** or **High** sign-in risk|*All users*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|
|**Enterprise**|Require multifactor authentication for **Low**, **Medium**, or **High** sign-in risk|*Executive staff group*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|
|**Specialized security**|Require multifactor authentication **always**|*Top Secret Project Buckeye group*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|

> [!TIP]
> Be careful when applying higher levels of protection to users and groups. The goal of security isn't to add unnecessary friction to the user experience. For example, members of the *Top Secret Project Buckeye group* are required to use MFA every time they sign in, even if they aren't working on the specialized content for their project. Excessive security friction can lead to fatigue. Enable [phishing-resistant authentication methods](/entra/identity/authentication/concept-authentication-passwordless) (for example, Windows Hello for Business or FIDO2 security keys) to help reduce the friction caused by security controls.

### Emergency access accounts

All organizations should have at least one emergency access account (and possibly more, depending on the size of the organization) that's monitored for use and excluded from policies. **These accounts are only used in case all other administrator accounts and authentication methods become locked out or otherwise unavailable**. For more information, see [Manage emergency access accounts in Microsoft Entra ID](/entra/identity/role-based-access-control/security-emergency-access).

### Exclusions

A recommended practice is to create a Microsoft Entra group for Conditional Access exclusions. This group gives you a means to provide access to a user while you troubleshoot access issues.

> [!WARNING]
> We recommend an exclusion group as a temporary solution only. Be sure to continuously monitor this group for changes and verify the group is being used only for its intended purpose.

Do the following steps to add an exclusion group to any existing policies. As previously described, you need [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) permissions.

1. In the Microsoft Entra admin center at <https://entra.microsoft.com>, go to **Protection** \> **Conditional Access** \> **Policies**. Or, to go directly to the **Conditional Access \| Policies** page, use <https://entra.microsoft.com/#view/Microsoft_AAD_ConditionalAccess/ConditionalAccessBlade/~/Policies/fromNav/Identity>.
2. On the **Conditional Access \| Policies** page, select an existing policy by clicking on the name value.
3. On the policy detail page that opens, select the link at **Users** in the **Assignments** section.
4. In the control that opens, select the **Exclude** tab, and then select **Users and groups**.
5. In the **Select excluded users and groups** flyout that opens, find and select the following identities:
   - **Users**: The emergency access accounts.
   - **Groups**: The Conditional Access exclusion group

   When you're finished on the **Select excluded users and groups** flyout, select **Select**

## Deployment

We recommend implementing the [starting point policies](#starting-point) in the order listed in the following table. You can implement the MFA policies for [enterprise](#enterprise) and [specialized security](#specialized-security) levels of protection at any time.

### Starting point

|Policy|More information|Licensing|
|---|---|---|
|[Require MFA when sign-in risk is *Medium* or *High*](#require-mfa-based-on-sign-in-risk)|Require MFA only when risk is detected by Microsoft Entra ID Protection.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
|[Block clients that don't support modern authentication](#block-clients-that-dont-support-multifactor-authentication)|Clients that don't use modern authentication can bypass Conditional Access policies, so it's important to block them.|Microsoft 365 E3 or E5|
|[High risk users must change password](#high-risk-users-must-change-password)|Force users to change their password when signing in if high-risk activity is detected for their account.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
|[Apply Application Protection Policies (APP) for data protection](#app-protection-policies)|One Intune APP per mobile device platform (Windows, iOS/iPadOS, and Android).|Microsoft 365 E3 or E5|
|[Require approved apps and app protection policies](#require-approved-apps-or-app-protection-policies)|Enforces app protection policies for mobile devices using iOS, iPadOS, or Android.|Microsoft 365 E3 or E5|

### Enterprise

|Policy|More information|Licensing|
|---|---|---|
|[Require MFA when sign-in risk is **Low**, **Medium**, or **High**](#require-mfa-based-on-sign-in-risk)|Require MFA only when risk is detected by Microsoft Entra ID Protection.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
|[Define device compliance policies](#device-compliance-policies)|Set minimum configuration requirements. One policy for each platform.|Microsoft 365 E3 or E5|
|[Require compliant PCs and mobile devices](#require-compliant-pcs-and-mobile-devices)|Enforces the configuration requirements for devices accessing your organization|Microsoft 365 E3 or E5|

### Specialized security

|Policy|More information|Licensing|
|---|---|---|
|[Require MFA **Always**](#always-require-mfa)|Users are required to do MFA anytime they sign in to services in the organization.|Microsoft 365 E3 or E5|

## App protection policies

[App protection policies](/mem/intune/apps/app-protection-policy) specify allowed apps and the actions they can take with your organization's data. Although there are many policies to choose from, the following list describes our recommended baselines.

> [!TIP]
> Although we provide three templates, most organizations should choose level 2 (maps to [starting point](#starting-point) or [enterprise](#enterprise) level security) and level 3 (maps to [specialized](#specialized-security) security).

- [Level 1 enterprise basic data protection](/mem/intune/apps/app-protection-framework#level-1-enterprise-basic-data-protection): We recommend this configuration as the minimum data protection for enterprise devices.
- **[Level 2 enterprise enhanced data protection](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration applies to most mobile users who access work or school data. Some of the controls might affect the user experience.
- **[Level 3 enterprise high data protection](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)**: We recommend this configuration in the following scenarios:
  - Organizations with larger or more sophisticated security teams.
  - Devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization

  Organizations likely targeted by well-funded and sophisticated attackers should aspire to this configuration.

### Create app protection policies

Create a new app protection policy for each device platform within Microsoft Intune (iOS/iPadOS and Android) using the data protection framework settings by doing the following steps:

- Manually create the policies by following the steps in [How to create and deploy app protection policies with Microsoft Intune](/mem/intune/apps/app-protection-policies).
- Import the sample [Intune App Protection Policy Configuration Framework JSON templates](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) with [Intune's PowerShell scripts](https://github.com/microsoftgraph/powershell-intune-samples).

## Device compliance policies

Intune device compliance policies define the requirements for devices in order to be compliant. You need to create a policy for each PC, phone, or tablet platform. This article covers recommendations for the following platforms:

- [Android](#enrollment-and-compliance-settings-for-android)
- [iOS/iPadOS](#enrollment-and-compliance-settings-for-iosipados)
- [Windows 10 and later](#recommended-compliance-settings-for-windows-10-and-later)

### Create device compliance policies

To create device compliance policies, do the following steps:

1. In the Microsoft Intune admin center at <https://endpoint.microsoft.com>, go to **Manage devices** \> **Compliance** \> **Policies** tab. Or, to go directly to the **Policies** tab of the **Devices \| Compliance** page, use <https://intune.microsoft.com/#view/Microsoft_Intune_DeviceSettings/DevicesMenu/~/compliance>.
2. On the **Policies** tab of the **Devices \| Compliance** page, select **Create policy**.

For step-by-step guidance, see [Create a compliance policy in Microsoft Intune](/mem/intune/protect/create-compliance-policy).

#### Enrollment and compliance settings for iOS/iPadOS

iOS/iPadOS supports several enrollment scenarios, two of which are covered by this framework:

- [Device enrollment for personally owned devices](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados#byod-user-and-device-enrollment): Personally owned devices (also known as bring your own device or BYOD) that are also used for work.
- [Automated device enrollment for corporate-owned devices](/mem/intune/enrollment/device-enrollment-program-enroll-ios): Organization-owned devices that are associated with a single user, and are used exclusively for work.

> [!TIP]
> As previously described, level 2 maps to [starting point](#starting-point) or [enterprise](#enterprise) level security, and level 3 maps to [specialized](#specialized-security) security. For more information, see [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

##### Compliance settings for personally enrolled devices

- [Personal basic security (Level 1)](/mem/intune/enrollment/ios-ipados-personal-device-security-configurations#personal-basic-security-level-1): We recommend this configuration as the minimum security for personal devices that access work or school data. You achieve this configuration by enforcing password policies, device lock characteristics, and disabling certain device functions (for example, untrusted certificates).
- **[Personal enhanced security (Level 2)](/mem/intune/enrollment/ios-ipados-personal-device-security-configurations#personal-enhanced-security-level-2)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables data sharing controls. This configuration applies to most mobile users who access work or school data.
- **[Personal high security (Level 3)](/mem/intune/enrollment/ios-ipados-personal-device-security-configurations#personal-high-security-level-3)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration enables stronger password policies, disables certain device functions, and enforces extra data transfer restrictions.

##### Compliance settings for automated device enrollment

- [Supervised basic security (Level 1)](/mem/intune/enrollment/ios-ipados-supervised-device-security-configurations#supervised-basic-security-level-1): We recommend this configuration as the minimum security for enterprise devices that access work or school data. You achieve this configuration by enforcing password policies, device lock characteristics, and disabling certain device functions (for example, untrusted certificates).
- **[Supervised enhanced security (Level 2)](/mem/intune/enrollment/ios-ipados-supervised-device-security-configurations#supervised-enhanced-security-level-2)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables data sharing controls and blocks access to USB devices. This configuration is applicable to most mobile users accessing work or school data on a device.
- **[Supervised high security (Level 3)](/mem/intune/enrollment/ios-ipados-supervised-device-security-configurations#supervised-high-security-level-3)** : We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration enables stronger password policies, disables certain device functions, enforces extra data transfer restrictions, and requires apps to be installed through Apple's volume purchase program.

#### Enrollment and compliance settings for Android

Android Enterprise supports several enrollment scenarios, two of which are covered by this framework:

- [Android Enterprise work profile](/mem/intune/enrollment/android-work-profile-enroll): Personally owned devices (also known as bring your own device or BYOD) that are also used for work. Policies controlled by the IT department ensure that work data can't be transferred into the personal profile.
- [Android Enterprise fully managed devices](/mem/intune/enrollment/android-fully-managed-enroll): Organization-owned devices that are associated with a single user, and are used exclusively for work.

The Android Enterprise security configuration framework is organized into several distinct configuration scenarios that provide guidance for work profile and fully managed scenarios.

> [!TIP]
> As previously described, level 2 maps to [starting point](#starting-point) or [enterprise](#enterprise) level security, and level 3 maps to [specialized](#specialized-security) security. For more information, see [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

##### Compliance settings for Android Enterprise work profile devices

- There's no basic security (level 1) offering for personally owned work profile devices. The available settings don't justify a difference between level 1 and level 2.
- **[Work profile enhanced security (Level 2)](/mem/intune/protect/compliance-policy-create-android-for-work#personally-owned-work-profile)**: We recommend this configuration as the minimum security for personal devices that access work or school data. This configuration introduces password requirements, separates work and personal data, and validates Android device attestation.
- **[Work profile high security (Level 3)](/mem/intune/protect/compliance-policy-create-android-for-work#personally-owned-work-profile)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration introduces mobile threat defense or Microsoft Defender for Endpoint, sets the minimum Android version, enables stronger password policies, and further separates work and personal data.

##### Compliance settings for Android Enterprise fully managed devices

- [Fully managed basic security (Level 1)](/mem/intune/fundamentals/protection-configuration-levels#level-1---minimum-protection-and-configuration): We recommend this configuration as the minimum security for an enterprise device. This configuration applies to most mobile users who work or school data. This configuration introduces password requirements, sets the minimum Android version, and enables specific device restrictions.
- **[Fully managed enhanced security (Level 2)](/mem/intune/fundamentals/protection-configuration-levels#level-2---enhanced-protection-and-configuration)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables stronger password policies and disables user/account capabilities.
- **[Fully managed high security (Level 3)](/mem/intune/fundamentals/protection-configuration-levels#level-3---high-protection-and-configuration)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration increases the minimum Android version, introduces mobile threat defense or Microsoft Defender for Endpoint, and enforces extra device restrictions.

#### Recommended compliance settings for Windows 10 and later

You configure the following settings as described in [Device Compliance settings for Windows 10/11 in Intune](/mem/intune/protect/compliance-policy-create-windows). These settings align with the principles outlined in [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

- **Device health \> Windows Health Attestation Service evaluation rules**: 

  |Property|Value|
  |---|---|
  |Require BitLocker|Require|
  |Require Secure Boot to be enabled on the device|Require|
  |Require code integrity|Require|

- **Device properties \> Operating System Version**: Specify appropriate values for operating system versions based on your IT and security policies.

  |Property|Value|
  |---|---|
  |Minimum OS version||
  |Maximum OS version||
  |Minimum OS required for mobile devices||
  |Maximum OS required for mobile devices||
  |Valid operating system builds||

- **Configuration Manager Compliance**:

  |Property|Value|
  |---|---|
  |Require device compliance from Configuration Manager|Select **Required** in environments that are co-managed with Configuration Manager. Otherwise, select **Not configured**.|

- **System security**:

  |Property|Value|
  |---|---|
  |**Password**||
  |&nbsp;&nbsp;Require a password to unlock mobile devices|Require|
  |&nbsp;&nbsp;Simple passwords|Block|
  |&nbsp;&nbsp;Password type|Device default|
  |&nbsp;&nbsp;Minimum password length|6|
  |&nbsp;&nbsp;Maximum inactivity in minutes before a password is required|15 minutes|
  |&nbsp;&nbsp;Password expiration (days)|41|
  |&nbsp;&nbsp;Number of previous passwords to prevent reuse|5|
  |&nbsp;&nbsp;Require password when device returns from idle state (Mobile and Holographic)|Require|
  |**Encryption**||
  |&nbsp;&nbsp;Require encryption of data storage on device|Require|
  |**Firewall**||
  |&nbsp;&nbsp;Firewall|Require|
  |**Antivirus**||
  |&nbsp;&nbsp;Antivirus|Require|
  |**Antispyware**||
  |&nbsp;&nbsp;Antispyware|Require|
  |**Defender**||
  |&nbsp;&nbsp;Microsoft Defender anti-malware|Require|
  |&nbsp;&nbsp;Microsoft Defender anti-malware minimum version|We recommend a value that's no more than five versions behind the most recent version.|
  |&nbsp;&nbsp;Microsoft Defender anti-malware signature up to date|Require|
  |&nbsp;&nbsp;Real-time protection|Require|

- **Microsoft Defender for Endpoint**:

  |Property|Value|
  |---|---|
  |[Require the device to be at or under the machine-risk score](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Medium|

## Conditional Access policies

After you create app protection policies and device compliance policies in Intune, you can enable enforcement with Conditional Access policies.

### Require MFA based on sign-in risk

Follow the guidance in: [Require multifactor authentication for elevated sign-in risk](/entra/identity/conditional-access/policy-risk-based-sign-in) to create a policy that requires multifactor authentication based on sign-in risk.

When configuring the policy, use the following risk levels:

|Protection level|Risk levels|
|---|---|---|
|Starting point|Medium and high|
|Enterprise|Low, medium, and high|

### Block clients that don't support multifactor authentication

Follow the guidance in: [Block legacy authentication with Conditional Access](/entra/identity/conditional-access/policy-block-legacy-authentication).

### High risk users must change password

Follow the guidance in: [Require a secure password change for elevated user risk](/entra/identity/conditional-access/policy-risk-based-user) to require users with compromised credentials to change their password.

Use this policy along with [Microsoft Entra password protection](/entra/identity/authentication/concept-password-ban-bad), which detects and blocks known weak passwords, their variants, and specific terms in your organization. Using Microsoft Entra password protection ensures that changed passwords are stronger.

### Require approved apps or app protection policies

You need to create a Conditional Access policy to enforce app protection policies that you create in Intune. Enforcing app protection policies requires a Conditional Access policy **and** a corresponding app protection policy.

To create a Conditional Access policy that requires approved apps or app protection, follow the steps in [Require approved client apps or app protection policy](/entra/identity/conditional-access/policy-all-users-approved-app-or-app-protection). This policy only allows accounts within apps protected by app protection policies to access Microsoft 365 endpoints.

Blocking legacy authentication for other apps on iOS/iPadOS and Android devices ensures that these devices can't bypass Conditional Access policies. By following the guidance in this article, you're already [blocking clients that don't support modern authentication](#block-clients-that-dont-support-multifactor-authentication).

### Require compliant PCs and mobile devices

> [!CAUTION]
> Verify that your own device is compliant before you enable this policy. Otherwise, you could get locked out and need to use an [emergency access account](#emergency-access-accounts) to recover your access.

Allow access to resources only after the device is determined to be compliant with your Intune compliance policies. For more information, see [Require device compliance with Conditional Access](/entra/identity/conditional-access/policy-all-users-device-compliance).

You can enroll new devices to Intune, even if you select **Require device to be marked as compliant** for **All users** and **All cloud apps** in the policy. **Require device to be marked as compliant** doesn't block Intune enrollment or access to the Microsoft Intune Web Company Portal app.

#### Subscription activation

If your organization uses [Windows subscription Activation](/windows/deployment/windows-subscription-activation) to enable users to "step-up" from one version of Windows to another, you should exclude the Universal Store Service APIs and Web Application (AppID: 45a330b1-b1ec-4cc1-9161-9f03992aa49f) from your device compliance.

### Always require MFA

Require MFA for all users by following the guidance in this article: [Require multifactor authentication for all users](/entra/identity/conditional-access/policy-all-users-mfa-strength).

## Next steps

[![Step 3: Policies for guest and external users.](media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](zero-trust-identity-device-access-policies-guest-access.md)

[Learn about policy recommendations for guest access](zero-trust-identity-device-access-policies-guest-access.md)
