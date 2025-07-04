---
title: "Step 1. Implement App Protection Policies"
ms.author: bcarter
author: brendacarter
f1.keywords:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
manager: dougeby
ms.date: 03/14/2025
audience: ITPro
ms.topic: how-to
description: Configure mobile app protection with App Protection policies (APP) to prevent specified corporate data from being copied and pasted to other apps. 
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

# Step 1. Implement app protection policies

Microsoft Intune app protection policies, sometimes referred to as Mobile Application Management (MAM), protect corporate data even if a device itself is not managed. This allows you to enable bring-your-own (BYO) and personal devices at work where users might be reluctant to "enroll" their device into management. App protection policies ensure corporate data in the apps you specify can't be copied and pasted to other apps on the device.

:::image type="content" source="media/devices/intune-app-steps.png" alt-text="Steps for creating App Protection Policies to separate organization and personal data on a device." lightbox="media/devices/intune-app-steps.png":::

In this illustration:

- With app protection policies, Intune creates a wall between your organization data and personal data. The app protection policies define which apps are allowed to access your data.
- If a user signs in with their organization credentials, Intune applies a policy at the app layer to prevent copy and paste of your organization data to personal apps and to require PIN access to this data.
- After creating an app protection policy, you enforce data protection with a Conditional Access policy.

This configuration greatly increases your security posture with almost no impact on the user experience. Employees can use apps like Microsoft Office and Microsoft Teams, that they know and love, while at the same time your organization can protect the data contained within the apps and devices.

If you have custom line-of-business applications that need protection, currently you can use the app wrapping tool to support using app protection policies with these applications. Or, you can integrate using the Intune App SDK. When your app has app protection policies applied to it, it can be managed by Intune and is recognized by Intune as a managed app. 

For more information about protecting your line-of-business applications using Intune, see [Prepare apps for mobile application management with Microsoft Intune](/mem/intune-service/developer/apps-prepare-mobile-application-management).

## Configuring mobile app protection

This guidance is tightly coordinated with the recommended [Zero Trust identity and device access policies](zero-trust-identity-device-access-policies-overview.md). After you create the mobile app protection policies in Intune, work with your identity team to configure the Conditional Access policies in Microsoft Entra ID that enforce mobile app protection. 

This illustration highlights the two policies (also described in the table following the illustration).

:::image type="content" source="media/devices/identity-device-starting-point.svg" alt-text="Highlighted Zero Trust identity and device access policies to enforce mobile app protection." lightbox="media/devices/identity-device-starting-point.svg":::

To configure these policies, use the recommended guidance and settings prescribed in [Zero Trust identity and device access policies](zero-trust-identity-device-access-policies-overview.md). The following table links directly to the instructions for configuring these policies in Intune and Microsoft Entra ID.

|Policy  |More information  |Licensing  |
|---------|---------|---------|
|  [Apply application protection policies for data protection](zero-trust-identity-device-access-policies-common.md#app-protection-policies)       | One Intune App Protection policy per platform (Windows, iOS/iPadOS, Android).        | Microsoft 365 E3 or E5        |
| [Require approved apps and app protection](zero-trust-identity-device-access-policies-common.md)       |  Enforces mobile app protection for phones and tablets using iOS, iPadOS, or Android.   |  Microsoft 365 E3 or E5       |

## Next step

Go to [Step 2. Enroll devices into management with Intune](manage-devices-with-intune-enroll.md). 
