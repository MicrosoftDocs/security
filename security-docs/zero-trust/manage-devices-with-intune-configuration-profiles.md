---
title: "Step 5. Deploy device profiles in Microsoft Intune"
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
ms.date: 03/14/2025
audience: ITPro
description: Get started with configuration profiles to enforce secure settings on devices using Intune to transition these security controls to the cloud.
ms.topic: how-to
ms.service: o365-solutions
ms.localizationpriority: high
ms.collection:
- highpri
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: 
keywords: 
---

# Step 5. Deploy device profiles in Microsoft Intune

Microsoft Intune includes settings and features you can enable or disable on different devices within your organization. These settings and features are added to "configuration profiles." You can create profiles for different devices and platforms, including iOS/iPadOS, Android device administrator, Android Enterprise, and Windows. Then, use Intune to apply or "assign" the profile to the devices.

This article provides guidance on getting started with configuration profiles.

:::image type="content" source="media/devices/intune-mdm-step-4.png" alt-text="The fourth step of Mobile Device Management to enforce secure settings on devices with configuration profiles." lightbox="media/devices/intune-mdm-step-4.png":::

Configuration profiles give you the ability to configure important protection and to bring devices into compliance so they can access your resources. Previously, these kinds of configuration changes were configured by using Group Policy settings in Active Directory Domain Services. A modern security strategy includes moving security controls to the cloud where enforcement of these controls isn't dependent on on-premises resources and access. Intune configuration profiles are the way to transition these security controls to the cloud.

To give you an idea of the kind of configuration profiles you can create, see [Apply features and settings on your devices using device profiles in Microsoft Intune](/mem/intune-service/configuration/device-profiles).

## Deploy Windows security baselines for Intune

As a starting point, if you want to align your device configurations to Microsoft security baselines, we recommend the security baselines within Microsoft Intune. The advantage of this approach is that you can rely on Microsoft to keep the baselines up to date as Windows features are released.

To deploy the Windows security baselines for Intune, available for Windows 10 and Windows 11. See [Use security baselines to configure Windows devices in Intune](/mem/intune-service/protect/security-baselines) to learn about the available baselines.

For now, just deploy the most appropriate MDM security baseline. See [Manage security baseline profiles in Microsoft Intune](/mem/intune-service/protect/security-baselines-configure)to create the profile and choose the baseline version.

Later, when Microsoft Defender for Endpoint is set up and connected to Intune, deploy the Defender for Endpoint baselines. This subject is covered in the next article in this series: [Step 6. Monitor device risk and compliance to security baselines](manage-devices-with-intune-monitor-risk.md).

It's important to understand that these security baselines aren't CIS or NIST compliant but closely mirror their recommendations. For more information, see [Are the Intune security baselines CIS or NIST compliant?](/mem/intune-service/protect/security-baselines#are-the-intune-security-baselines-cis-or-nist-compliant).

## Customize configuration profiles for your organization

In addition to deploying the pre-configured baselines, many enterprise-scale organizations implement configuration profiles for more granular control. This configuration helps reduce the dependency on Group Policy Objects (GPOs) in the on-premises Active Directory environment and move security controls to the cloud.

The many settings you can configure by using configuration profiles can be grouped into four categories, as seen in the following illustration.

:::image type="content" source="media/devices/intune-device-profile-categories.png" alt-text="Intune device profile categories including device features, device restrictions, access configuration, and custom settings." lightbox="media/devices/intune-device-profile-categories.png":::

The following table describes the illustration.

|Category |Description |Examples  |
|---------|---------|---------|
|Device features     | Controls features on the device. This category only applies to iOS/iPadOS and macOS devices.        | Airprint, notifications, lock screen messages        |
|Device restrictions     | Controls security, hardware, data sharing, and more settings on the devices        | Require a PIN, data encryption        |
|Access configuration     |  Configures a device to access your organization’s resources        | Email profiles, VPN profiles, Wi-Fi settings, certificates        |
|Custom     | Set custom configuration or execute custom configuration actions       | Set OEM settings, execute PowerShell scripts        |
|    |         |         |

When customizing configuration profiles for your organization, use the following guidance:

- Simplify your security governance strategy by keeping the overall number of policies small.
- Group settings into the categories listed in the preceding table, or use categories that make sense for your organization.
- When moving security controls from GPOs to Intune configuration profiles, consider whether the settings configured by each GPO are still relevant and required to contribute to your overall cloud security strategy. Conditional Access and the many policies that can be configured across cloud services, including Intune, provide more sophisticated protection than could be configured in an on-premises environment where custom GPOs were originally designed.
- Utilize Group Policy Analytics to compare and map your current GPO settings to capabilities within Microsoft Intune. See [Analyze your on-premises group policy objects (GPO) using Group Policy analytics](/mem/intune-service/configuration/group-policy-analytics) in Microsoft Intune.
- When utilizing custom configuration profiles, be sure to use the guidance at [Create a profile with custom settings in Intune](/mem/intune-service/configuration/custom-settings-configure).

## Additional resources

If you're not sure where to start with device profiles, the following resources can help:

- [Guided scenarios](/mem/intune-service/fundamentals/guided-scenarios-overview) 
- [Security baselines](/mem/intune-service/protect/security-baselines)

If your environment includes on-premises GPOs, the following features are a good transition to the cloud:

- [Group Policy analytics](/mem/intune-service/configuration/group-policy-analytics)
- [Admin templates (ADMX)](/mem/intune-service/configuration/administrative-templates-windows)
- [Settings Catalog](/mem/intune-service/configuration/settings-catalog)

## Next step

Go to [Step 6. Monitor device risk and compliance to security baselines](manage-devices-with-intune-monitor-risk.md).
