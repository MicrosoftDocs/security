---
title: Zero Trust Identity and Device Access Policies for Microsoft 365
description: Learn about Zero Trust identity and device access policies for Microsoft 365, including configurations and benefits for secure deployments.
ms.author: kenwith
author: kenwith

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
ms.date: 06/18/2025
---

# Common security policies for Microsoft 365 organizations

Many organizations have questions when deploying Microsoft 365 in a secure fashion. The Conditional Access, app protection, and device compliance policies in this article are based on Microsoft's recommendations and the three guiding principles of [Zero Trust](zero-trust-overview.md):

- Verify explicitly
- Use least privilege
- Assume breach

Organizations can use these policies as is or customize them to fit their needs. Test your policies in a nonproduction environment to identify potential effects and communicate them to users before rolling them out to production. Testing is critical to identify and communicate possible effects to users.

We group these policies into three protection levels based on where you are on your deployment journey:

- **Starting point**: Basic controls that introduce multifactor authentication, secure password changes, and Intune app protection policies for mobile devices.
- **Enterprise**: Enhanced controls that introduce device compliance.
- **Specialized security**: Policies that require multifactor authentication every time for specific data sets or users.

This diagram shows the protection levels for each policy and the types of devices they apply to:

:::image type="content" source="media/microsoft-365-policies-configurations/identity-device-access-policies-three-tiers.svg" alt-text="A diagram showing common identity and device policies that support Zero Trust principles." lightbox="media/microsoft-365-policies-configurations/identity-device-access-policies-three-tiers.svg":::

You can download this diagram as a [PDF](https://download.microsoft.com/download/3d22de2e-38d8-4119-9f26-f6122b567909/zero-trust-id-and-device-access-policies-contoso.pdf) file or an editable [Visio](https://download.microsoft.com/download/8/b/2/8b23ab16-a3de-4b4e-b8a0-95b393cfbcee/zero-trust-id-and-device-access-policies-contoso.vsdx) file.

> [!TIP]
> Require multifactor authentication (MFA) for users before enrolling devices in Intune to confirm the device is with the intended user. MFA is on by default thorough [security defaults](/entra/fundamentals/security-defaults#enforced-security-policies), or you can use Conditional Access policies to [require MFA for all users](/entra/identity/conditional-access/policy-all-users-mfa-strength).
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

Ensure users register for MFA before they're required to use it. If your licenses include Microsoft Entra ID P2, you can use the [MFA registration policy within Microsoft Entra ID Protection](/entra/id-protection/howto-identity-protection-configure-mfa-policy) to require users to register. We provide [communication templates](https://aka.ms/mfatemplates) that you can download and customize to promote user registration.

### Groups

All Microsoft Entra groups used in these recommendations must be Microsoft 365 Groups, **not** security groups. This requirement is important for the deployment of sensitivity labels to secure documents in Microsoft Teams and SharePoint. For more information, see [Learn about groups and access rights in Microsoft Entra ID](/entra/fundamentals/concept-learn-about-groups#group-types).

### Assigning policies

You can assign Conditional Access policies to users, groups, and administrator roles. You can assign Intune app protection and device compliance policies to *groups only*. Before you configure your policies, identify who should be included and excluded. Typically, starting point protection level policies apply to everyone in the organization.

The following table describes example group assignments and exclusions for MFA after users complete [user registration](#user-registration):

|&nbsp;|Microsoft Entra Conditional Access policy|Include|Exclude|
|---|---|:---:|---|
|**Starting point**|Require multifactor authentication for **Medium** or **High** sign-in risk|*All users*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|
|**Enterprise**|Require multifactor authentication for **Low**, **Medium**, or **High** sign-in risk|*Executive staff group*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|
|**Specialized security**|Require multifactor authentication **always**|*Top Secret Project Buckeye group*|<ul><li>Emergency access accounts</li><li>Conditional Access exclusion group</li></ul>|

> [!TIP]
> Apply higher levels of protection to users and groups carefully. Security's goal isn't to add unnecessary friction to the user experience. For example, members of the *Top Secret Project Buckeye group* are required to use MFA every time they sign in, even if they aren't working on the specialized content for their project. Excessive security friction can lead to fatigue. Enable [phishing-resistant authentication methods](/entra/identity/authentication/concept-authentication-passwordless) (for example, Windows Hello for Business or FIDO2 security keys) to help reduce the friction caused by security controls.

### Emergency access accounts

Every organization needs at least one emergency access account that is monitored for use and excluded from policies. Larger organizations might require more accounts. **These accounts are only used in case all other administrator accounts and authentication methods become locked out or otherwise unavailable**. For more information, see [Manage emergency access accounts in Microsoft Entra ID](/entra/identity/role-based-access-control/security-emergency-access).

### Excluding users

We recommend crating a Microsoft Entra group for Conditional Access exclusions. This group gives you a means to provide access to a user while you troubleshoot access issues. Features like access reviews in Microsoft Entra ID Governance help you [manage users excluded from Conditional Access policies](/entra/id-governance/conditional-access-exclusion)

> [!WARNING]
> We recommend an exclusion group as a temporary solution only. Continuously monitor this group for changes and ensure it's used only for its intended purpose.

Use the following steps to add an exclusion group to existing policies. 

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Protection** > **Conditional Access** > **Policies**.
3. Select an existing policy by clicking on the name.
4. Under **Assignments**, select **Users or workload identities**.
   a. Under **Exclude**, select **Users and groups**, and choose the following identities:
      - **Users**: Your emergency access accounts.
      - **Groups**: Your Conditional Access exclusion group.
   b. Select **Select**.
5. Make any other modifications.
6. Select **Save**.


### Excluding applications

We recommend creating a baseline multifactor authentication policy targeting all users and all resources (without any application exclusions), like the one explained in [Require multifactor authentication for all users](/entra/identity/conditional-access/policy-all-users-mfa-strength). Excluding certain applications might have unintended security and usability consequences described in [Conditional Access behavior when an all resources policy has an app exclusion](/entra/identity/conditional-access/concept-conditional-access-cloud-apps#conditional-access-behavior-when-an-all-resources-policy-has-an-app-exclusion). Applications, like Microsoft 365 and Microsoft Teams, depend on multiple services making behavior unpredictable when exclusions are made.

## Deployment

We recommend implementing the starting point policies in the order listed in the following table. You can implement the MFA policies for enterprise and specialized security levels of protection at any time.

**Starting point**:

  |Policy|More information|Licensing|
  |---|---|---|
  |[Require MFA when sign-in risk is *Medium* or *High*](#require-mfa-based-on-sign-in-risk)|Require MFA only when risk is detected by Microsoft Entra ID Protection.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
  |[Block clients that don't support modern authentication](#block-clients-that-dont-support-multifactor-authentication)|Clients that don't use modern authentication can bypass Conditional Access policies, so it's important to block them.|Microsoft 365 E3 or E5|
  |[High risk users must change password](#high-risk-users-must-change-password)|Force users to change their password when signing in if high-risk activity is detected for their account.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
  |[Apply Application Protection Policies (APP) for data protection](#app-protection-policies)|One Intune APP per mobile device platform (Windows, iOS/iPadOS, and Android).|Microsoft 365 E3 or E5|
  |[Require approved apps and app protection policies](#require-approved-apps-or-app-protection-policies)|Enforces app protection policies for mobile devices using iOS, iPadOS, or Android.|Microsoft 365 E3 or E5|

**Enterprise**:

  |Policy|More information|Licensing|
  |---|---|---|
  |[Require MFA when sign-in risk is **Low**, **Medium**, or **High**](#require-mfa-based-on-sign-in-risk)|Require MFA only when risk is detected by Microsoft Entra ID Protection.|<ul><li>Microsoft 365 E5</li><li>Microsoft 365 E3 with the E5 Security add-on</li><li>Microsoft 365 with EMS E5</li><li>Individual Microsoft Entra ID P2 licenses</li></ul>|
  |[Define device compliance policies](#device-compliance-policies)|Set minimum configuration requirements. One policy for each platform.|Microsoft 365 E3 or E5|
  |[Require compliant PCs and mobile devices](#require-compliant-pcs-and-mobile-devices)|Enforces the configuration requirements for devices accessing your organization|Microsoft 365 E3 or E5|

**Specialized security**:

  |Policy|More information|Licensing|
  |---|---|---|
  |[Require MFA **Always**](#always-require-mfa)|Users are required to do MFA anytime they sign in to services in the organization.|Microsoft 365 E3 or E5|

## App protection policies

[App protection policies](/intune/intune-service/apps/app-protection-policy) specify allowed apps and the actions they can take with your organization's data. Although there are many policies to choose from, the following list describes our recommended baselines.

> [!TIP]
> Although we provide three templates, most organizations should choose Level 2 (maps to [starting point](#deployment) or [enterprise](#deployment) level security) and Level 3 (maps to [specialized](#deployment) security).

- [Level 1 enterprise basic data protection](/intune/intune-service/apps/app-protection-framework#level-1-enterprise-basic-data-protection): We recommend this configuration as the minimum data protection for enterprise devices.
- **[Level 2 enterprise enhanced data protection](/intune/intune-service/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration applies to most mobile users who access work or school data. Some of the controls might affect the user experience.
- **[Level 3 enterprise high data protection](/intune/intune-service/apps/app-protection-framework#level-3-enterprise-high-data-protection)**: We recommend this configuration in the following scenarios:
  - Organizations with larger or more sophisticated security teams.
  - Devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization

  Organizations likely targeted by well-funded and sophisticated attackers should aspire to this configuration.

Create a new app protection policy for each device platform within Microsoft Intune (iOS/iPadOS and Android) using the data protection framework settings by using either of the following methods:

- Manually create the policies by following the steps in [How to create and deploy app protection policies with Microsoft Intune](/intune/intune-service/apps/app-protection-policies).
- Import the sample [Intune App Protection Policy Configuration Framework JSON templates](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) with [Intune's PowerShell scripts](https://github.com/microsoftgraph/powershell-intune-samples).

## Device compliance policies

Intune device compliance policies define the requirements for devices to be compliant. You need to create a policy for each PC, phone, or tablet platform. The following sections describe the recommendations for the following platforms:

- [Android](#enrollment-and-compliance-settings-for-android)
- [iOS/iPadOS](#enrollment-and-compliance-settings-for-iosipados)
- [Windows 10 and later](#recommended-compliance-settings-for-windows-10-and-later)

### Create device compliance policies

Follow these steps to create device compliance policies:

1. Sign in to the [Microsoft Intune admin center](https://intune.microsoft.com/) as an [Intune Administrator](/entra/identity/role-based-access-control/permissions-reference#intune-administrator).
2. Browse to **Devices** > **Compliance** > **Create policy**.

For step-by-step guidance, see [Create a compliance policy in Microsoft Intune](/intune/intune-service/protect/create-compliance-policy).

### Enrollment and compliance settings for iOS/iPadOS

iOS/iPadOS supports several enrollment scenarios, two of which are covered by this framework:

- [Device enrollment for personally owned devices](/intune/intune-service/fundamentals/deployment-guide-enrollment-ios-ipados#byod-user-and-device-enrollment): Personally owned devices (also known as bring your own device or BYOD) that are also used for work.
- [Automated device enrollment for corporate-owned devices](/intune/intune-service/enrollment/device-enrollment-program-enroll-ios): Organization-owned devices that are associated with a single user, and are used exclusively for work.

> [!TIP]
> As previously described, Level 2 maps to [starting point](#deployment) or [enterprise](#deployment) level security, and Level 3 maps to [specialized](#deployment) security. For more information, see [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

#### Compliance settings for personally enrolled devices

- [Personal basic security (Level 1)](/mem/intune-service/protect/ios-ipados-personal-device-security-configurations#personal-basic-security-level-1): We recommend this configuration as the minimum security for personal devices that access work or school data. You achieve this configuration by enforcing password policies, device lock characteristics, and disabling certain device functions (for example, untrusted certificates).
- **[Personal enhanced security (Level 2)](/mem/intune-service/protect/ios-ipados-personal-device-security-configurations#personal-enhanced-security-level-2)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables data sharing controls. This configuration applies to most mobile users who access work or school data.
- **[Personal high security (Level 3)](/mem/intune-service/protect/ios-ipados-personal-device-security-configurations#personal-high-security-level-3)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration enables stronger password policies, disables certain device functions, and enforces extra data transfer restrictions.

#### Compliance settings for automated device enrollment

- [Supervised basic security (Level 1)](/mem/intune-service/protect/ios-ipados-supervised-device-security-configurations#supervised-basic-security-level-1): We recommend this configuration as the minimum security for enterprise devices that access work or school data. You achieve this configuration by enforcing password policies, device lock characteristics, and disabling certain device functions (for example, untrusted certificates).
- **[Supervised enhanced security (Level 2)](/mem/intune-service/protect/ios-ipados-supervised-device-security-configurations#supervised-enhanced-security-level-2)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables data sharing controls and blocks access to USB devices. This configuration is applicable to most mobile users accessing work or school data on a device.
- **[Supervised high security (Level 3)](/mem/intune-service/protect/ios-ipados-supervised-device-security-configurations#supervised-high-security-level-3)** : We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration enables stronger password policies, disables certain device functions, enforces extra data transfer restrictions, and requires apps to be installed through Apple's volume purchase program.

### Enrollment and compliance settings for Android

Android Enterprise supports several enrollment scenarios, two of which are covered by this framework:

- [Android Enterprise work profile](/intune/intune-service/enrollment/android-work-profile-enroll): Personally owned devices (also known as bring your own device or BYOD) that are also used for work. Policies controlled by the IT department ensure that work data can't be transferred into the personal profile.
- [Android Enterprise fully managed devices](/intune/intune-service/enrollment/android-fully-managed-enroll): Organization-owned devices that are associated with a single user, and are used exclusively for work.

The Android Enterprise security configuration framework is organized into several distinct configuration scenarios that provide guidance for work profile and fully managed scenarios.

> [!TIP]
> As previously described, Level 2 maps to [starting point](#deployment) or [enterprise](#deployment) level security, and Level 3 maps to [specialized](#deployment) security. For more information, see [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

#### Compliance settings for Android Enterprise work profile devices

- There's no basic security (Level 1) offering for personally owned work profile devices. The available settings don't justify a difference between Level 1 and Level 2.
- **[Work profile enhanced security (Level 2)](/intune/intune-service/protect/android-personally-owned-security-configurations#personally-owned-work-profile-enhanced-security-level-2)**: We recommend this configuration as the minimum security for personal devices that access work or school data. This configuration introduces password requirements, separates work and personal data, and validates Android device attestation.
- **[Work profile high security (Level 3)](/intune/intune-service/protect/android-personally-owned-security-configurations#personally-owned-work-profile-high-security-level-3)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration introduces mobile threat defense or Microsoft Defender for Endpoint, sets the minimum Android version, enables stronger password policies, and further separates work and personal data.

#### Compliance settings for Android Enterprise fully managed devices

- [Fully managed basic security (Level 1)](/intune/intune-service/protect/android-fully-managed-security-configurations#fully-managed-basic-security-level-1): We recommend this configuration as the minimum security for an enterprise device. This configuration applies to most mobile users who work or school data. This configuration introduces password requirements, sets the minimum Android version, and enables specific device restrictions.
- **[Fully managed enhanced security (Level 2)](/intune/intune-service/protect/android-fully-managed-security-configurations#fully-managed-enhanced-security-level-2)**: We recommend this configuration for devices that access sensitive data or confidential information. This configuration enables stronger password policies and disables user/account capabilities.
- **[Fully managed high security (Level 3)](/intune/intune-service/protect/android-fully-managed-security-configurations#fully-managed-high-security-level-3)**: We recommend this configuration for devices used by specific users or groups who are at uniquely high risk. For example, users who handle highly sensitive data where unauthorized disclosure would cause considerable loss to the organization. This configuration increases the minimum Android version, introduces mobile threat defense or Microsoft Defender for Endpoint, and enforces extra device restrictions.

### Recommended compliance settings for Windows 10 and later

Configure the following settings as described in [Device Compliance settings for Windows 10/11 in Intune](/intune/intune-service/protect/compliance-policy-create-windows). These settings align with the principles outlined in [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).

- **Device health** > **Windows Health Attestation Service evaluation rules**: 

  |Property|Value|
  |---|---|
  |Require BitLocker|Require|
  |Require Secure Boot to be enabled on the device|Require|
  |Require code integrity|Require|

- **Device properties** > **Operating System Version**: Enter appropriate values for operating system versions based on your IT and security policies.

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
  |[Require the device to be at or under the machine-risk score](/intune/intune-service/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Medium|

## Conditional Access policies

After you create app protection policies and device compliance policies in Intune, you can enable enforcement with Conditional Access policies.

### Require MFA based on sign-in risk

Follow the guidance in: [Require multifactor authentication for elevated sign-in risk](/entra/identity/conditional-access/policy-risk-based-sign-in) to create a policy that requires multifactor authentication based on sign-in risk.

When configuring the policy, use the following risk levels:

|Protection level|Risk levels|
|---|---|---|
|Starting point|Medium and High|
|Enterprise|Low, Medium, and High|

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
> Verify your own device is compliant before you enable this policy. Otherwise, you could get locked out and need to use an [emergency access account](#emergency-access-accounts) to recover your access.

Allow access to resources only after the device is determined to be compliant with your Intune compliance policies. For more information, see [Require device compliance with Conditional Access](/entra/identity/conditional-access/policy-all-users-device-compliance).

You can enroll new devices to Intune, even if you select **Require device to be marked as compliant** for **All users** and **All cloud apps** in the policy. **Require device to be marked as compliant** doesn't block Intune enrollment or access to the Microsoft Intune Web Company Portal app.

#### Subscription activation

If your organization uses [Windows subscription Activation](/windows/deployment/windows-subscription-activation) to enable users to "step-up" from one version of Windows to another, you should exclude the Universal Store Service APIs and Web Application (AppID: 45a330b1-b1ec-4cc1-9161-9f03992aa49f) from your device compliance.

### Always require MFA

Require MFA for all users by following the guidance in this article: [Require multifactor authentication for all users](/entra/identity/conditional-access/policy-all-users-mfa-strength).

## Next steps

[![Step 3: Policies for guest and external users.](media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](zero-trust-identity-device-access-policies-guest-access.md)

[Learn about policy recommendations for guest access](zero-trust-identity-device-access-policies-guest-access.md)
