---
title: Secure endpoints with Zero Trust
description: Not all endpoints are managed or even owned by the organization, leading to different device configurations and software patch levels. In a Zero Trust approach, the same security policies are applied regardless of the type of device or who owns it. 
ms.date: 06/25/2025
ms.service: zero-trust
author: garycentric
ms.author: brenduns
ms.topic: conceptual
ms.collection:
  - zerotrust-pillar
ms.custom: sfi-image-nochange
---


# Secure endpoints with Zero Trust

:::image type="icon" source="../media/icon-endpoints-medium.png":::

The modern enterprise has an incredible diversity of endpoints that access data. Not all endpoints are managed or even owned by the organization, leading to different device configurations and software patch levels. This creates a massive attack surface and, if left unresolved, the access of work data from untrusted endpoints can easily become the weakest link in your Zero Trust security strategy. *(Download the Zero Trust Maturity Model: [Zero_Trust_Vision_Paper_Final 10.28.pdf](https://go.microsoft.com/fwlink/p/?LinkID=2109181).)*

Zero Trust adheres to the principle, "Never trust, always verify." In terms of endpoints, this means always verify *all* endpoints. That includes not only contractor, partner, and guest devices, but also [apps](https://aka.ms/ZTApplications) and devices used by employees to access work data, regardless of device ownership.

In a Zero Trust approach, the same security policies are applied regardless of whether the device is corporate-owned or personally owned through bring your own device (BYOD); whether the device is fully managed by IT, or only the apps and data are secured. The policies apply to all endpoints, whether PC, Mac, smartphone, tablet, wearable, or IoT device wherever they are connected, be it the secure corporate [network](https://aka.ms/ZTNetwork), home broadband, or public internet.
Most importantly, the health and trustworthiness of apps that run on those endpoints impacts your security posture. You need to prevent corporate data from leaking to untrusted or unknown apps or services, either accidentally or through malicious intent.

**There are a few key rules for securing devices and endpoints in a Zero Trust model:**
Zero Trust security policies are centrally enforced through the cloud and cover endpoint security, device configuration, app protection, device compliance, and risk posture.

- The platform as well as the apps that run on the devices are securely provisioned, properly configured, and kept up to date.
- There is automated and prompt response to contain access to corporate data within the apps in case of a security compromise.
- The access control system ensures that all policy controls are in effect before the data is accessed.

## Zero Trust deployment objectives for securing endpoints

Before most organizations start the Zero Trust journey, their endpoint security is set up as follows:

- Endpoints are domain-joined and managed with solutions like Group Policy Objects or Configuration Manager. These are great options, but they don't leverage modern Windows *Configuration Service Providers* (CSPs) or require a separate cloud management gateway appliance to service cloud-based devices.
- Endpoints are required to be on a corporate network to access data. This could mean that the devices are required to physically be on-site to access the corporate network, or that they require VPN access, which increases the risk that a compromised device could access sensitive corporate resources.

When implementing an end-to-end Zero Trust framework for securing endpoints, we recommend you focus first on the three initial deployment objectives. After those are completed, focus on the fourth objective:

1. [**Endpoints are registered with cloud identity providers**](/security/zero-trust/deploy/endpoints#i-endpoints-are-registered-with-a-cloud-identity-providers). In order to monitor security and risk across multiple endpoints used by any one person, you need [visibility](https://aka.ms/ZTCrossPillars) to all devices and access points that might have access to your resources. On registered devices you can then enforce a baseline of security that also provides users a biometric or PIN based method for authentication to help eliminate reliance on passwords.

2. [**Access is only granted to cloud-managed and compliant endpoints and apps**](https://aka.ms/ZTCrossPillars). Set compliance rules to ensure that devices meet minimum security requirements before access is granted. Also, create remediation rules and notifications for noncompliant devices so that people know how to resolve compliance issues.

3. [**Data loss prevention (DLP) policies are enforced for corporate devices and BYOD**](/security/zero-trust/deploy/endpoints#iii-data-loss-prevention-dlp-policies-are-enforced-for-corporate-devices-and-byod). Control what the user can do with the data after they have access. For instance, restrict file saving to untrusted locations (like a local disk), or restrict copy-and-paste sharing with a consumer communication app or chat app to protect data.

4. [**Endpoint threat detection is used to monitor device risk**](/security/zero-trust/deploy/endpoints#iv-endpoint-threat-detection-is-used-to-monitor-device-risk). Aim for a single pane of glass solution to manage all endpoints in a consistent way. Use a security information and event management (SIEM) solution to route endpoint logs and transactions such that you get fewer, but actionable, alerts.

As a final task, examine [Zero Trust principles for IoT and operational technology networks](#zero-trust-and-your-ot-networks).

## Endpoint Zero Trust deployment guide

This guide walks you through the steps required to secure your devices following the principles of a Zero Trust security framework.

### 1. Register endpoints with a cloud identity provider

To help limit risk exposure, monitor endpoints to ensure each one has a trusted identity, core security requirements are applied, and the risk level for things like malware or data exfiltration has been measured, remediated, or deemed acceptable.

After a device registers, users can access your organization's restricted resources using their corporate username and password to sign in. When available, increase security through use of capabilities like Windows Hello for Business.

![Diagram of the steps within phase 1 of the initial deployment objectives.](../media/endpoints/diagram-steps-box-endpoints-1.png)

#### Register corporate devices with Microsoft Entra ID

Have the Windows devices that are used to access your organizations data, join and register with Microsoft Entra ID through one of the following paths:
- **Windows out-of-box-experience** – Using the out-of-box experience (OOBE) to join Windows devices to Microsoft Entra ID simplifies setup, ensuring devices are ready for secure access to organizational resources immediately. For guidance, see [Microsoft Entra join a new Windows device](/entra/identity/devices/device-join-out-of-box).

- **Previously provisioned Windows devices** – Users of a previously provisioned Windows work device can use their Work or School account to register it with Microsoft Entra ID. See [Add Your Work or School Account to a Windows Device](https://support.microsoft.com/windows/add-your-work-or-school-account-to-a-windows-device-a6505ceb-1a20-4b15-889c-250175481506).

- **Register a personal device** - Users can register their personal Windows devices with Microsoft Entra ID. See [Register your personal device on your work or school network](https://support.microsoft.com/account-billing/register-your-personal-device-on-your-work-or-school-network-8803dd61-a613-45e3-ae6c-bd1ab25bf8a8).

For corporate owned devices you can use the following platform-specific methods to provision new operating systems and register devices with Microsoft Entra ID:

- **Windows** – Windows Autopilot is a collection of technologies used to set up and pre-configure new devices, getting them ready for productive use. See [Overview of Windows Autopilot](/autopilot/overview).

- **iOS/iPadOS** - Corporate-owned devices purchased through Apple Business Manager or Apple School Manager can be enrolled in Intune via automated device enrollment. See [Set up Automated Device Enrollment](/intune/intune-service/enrollment/device-enrollment-program-enroll-ios).

#### Enhance authentication security with Windows Hello for Business

To allow users an alternative sign-in method that replaces use of passwords with strong two-factor authentication on devices and enforce rules for the use of PINs, security keys for sign-in and more, enable [Windows Hello for Business on users' Windows devices](/intune/intune-service/protect/windows-hello). 

Microsoft Intune supports two complimentary methods to apply and enforce Windows Hello for Business settings:

- **At device enrollment with tenant-wide policy** – Use this method to apply a default Windows Hello for Business policy to each Windows device when it enrolls with Intune. This policy helps ensure every new Windows device that joins your organization is held to the same initial configuration standards for PIN requirements, two-factor authentication, and more.

  For more information and configuration guidance, see [Windows Hello at device enrollment](/intune/intune-service/protect/windows-hello) in the Intune documentation.

- **After enrollment with Account protection profiles** – Account protection profiles allow you to apply specific Windows Hello for Business configurations to different groups within your organization after they have enrolled with Intune. If there is a conflict between the account protection profile and the tenant-wide profile, the account protection profile takes precedence. This enables adjustments to be made for different groups based on their requirements.

  [Intune Account protection *profiles*](/intune/intune-service/protect/endpoint-security-account-protection-policy#account-protection-profiles) are one type of profile for the Account Protection *policy* type, which in turn is one type of Intune endpoint security policy. For guidance in configuring this profile, see [Create an endpoint security policy](/intune/intune-service/protect/endpoint-security-policy#create-an-endpoint-security-policy), and choose the Account protection *policy* type, followed by the Account protection *profile* type.

### 2. Limit access to cloud-managed and compliant endpoints and apps

With identities for endpoints that join your organization established and enhanced authentication requirements in place, ensure those endpoints meet your organization’s security expectations before they’re used to access your organization’s data and resources.

To gate access, use Intune [device compliance policies](/intune/intune-service/protect/device-compliance-get-started), which work with Microsoft Entra Conditional Access to ensure only devices that are currently compliant to your security requirements can be used by your authenticated users to access resources. An important part of compliance policies are [remediation notifications and rules](/intune/intune-service/protect/actions-for-noncompliance) that help users bring a noncompliant device back into compliance.

:::image type="content" source="../media/endpoints/diagram-steps-box-endpoints-2.png" alt-text="Diagram of the steps within phase 2 of the initial deployment objectives." border="true":::

#### Create a compliance policy with Microsoft Intune

Microsoft Intune compliance policies are sets of rules and conditions that you use to evaluate the configuration of your managed devices. These policies can help you secure organizational data and resources from devices that don't meet those configuration requirements. Managed devices must satisfy the conditions you set in your policies to be considered compliant by Intune.

Intune device compliance has two parts that work together:

- **Compliance policy settings** are a single set of configurations that apply tenant-wide to provide a built-in compliance policy that every device receives. Compliance policy settings establish how compliance policy works in your environment, including how to handle devices that aren't assigned an explicit device compliance policy.

  To configure these tenant-wide settings, see [Compliance policy settings](/intune/intune-service/protect/device-compliance-get-started#compliance-policy-settings). 

- **Device compliance policies** are discrete sets of platform-specific rules and settings you deploy to groups of users or devices. Devices evaluate the rules in the policy to report on their compliance status. A noncompliant status can result in one or more actions for noncompliance. Microsoft Entra Conditional Access policies can also use that status to block access to organizational resources from that device.

  To configure groups with device compliance policies, see [Create a compliance policy in Microsoft Intune](/intune/intune-service/protect/create-compliance-policy). For examples of increasing levels of compliance configurations you can use, see Intune’s [Plan for compliance policies](/intune/intune-service/fundamentals/deployment-plan-compliance-policies).

#### Establish actions and user facing notifications for noncompliant devices

Each Intune compliance policy includes *Actions for noncompliance*. The actions apply when a device fails to meet its assigned compliance policy configuration. Both Intune and Conditional Access read a device’s status to help determine additional steps you can configure or to block access to organizations resources from that device for as long as it remains noncompliant.

You configure Actions for noncompliance as part of each device compliance policy you create.

Actions for noncompliance include but are not limited to the following options, with different options available for different platforms:

- Mark the device as noncompliant
- Send a preconfigured email to the device’s user
- Remotely lock the device
- Send a preconfigured push notification to the user

To learn about available actions, how to add them to policies, and how to preconfigure emails and notifications, see [Configure actions for noncompliant devices in Intune](/intune/intune-service/protect/actions-for-noncompliance).

### 3. Deploy policies that enforce data loss prevention (DLP) for corporate devices and BYOD

Once data access is granted, you want to control what the user can do with the data and how it is stored. For example, if a user accesses a document with their corporate identity, you want to prevent that document from being saved in an unprotected consumer storage location, or from being shared with a consumer communication or chat app.

:::image type="content" source="../media/endpoints/diagram-steps-box-endpoints-3.png" alt-text="Diagram of the steps within phase 3 of the initial deployment objectives." border="true":::

#### Apply recommended security settings

Security baselines can help establish a broad and consistent baseline of secure configurations that help protect users, devices, and data. Intune’s Security baselines are preconfigured groups of Windows settings that help you apply a known group of settings and default values that are recommended by the relevant security teams. You can use these baselines with their default configurations or edit them to create customized instances that meet the varied needs of different groups in your organization.

See [Use security baselines to help secure Windows devices you manage with Microsoft Intune](/intune/intune-service/protect/security-baselines).

#### Deploy updates automatically to endpoints

To keep managed devices in compliance with evolving security threats, use Intune policies that can automate update deployments:

- **Windows Updates for Business** – You can use Intune policies for Windows Updates for Business to automatically install Windows updates on your devices. Policies can automate when updates install and the type of updates, including the Windows version, the latest security updates, and new drivers. To get started, see [Manage Windows 10 and Windows 11 software updates in Intune](/intune/intune-service/protect/windows-update-for-business-configure).

- **Android Enterprise updates** – Intune supports [automatic over-the-air updates](/intune/intune-service/protect/zebra-lifeguard-ota-integration) to the operating system and firmware for Zebra Android devices through a partner integration.

- **iOS/iPadOS** - Intune policies can automatically install updates on iOS/iPad devices that are enrolled as a  [supervised device](/intune/intune-service/enrollment/device-enrollment-program-enroll-ios#what-is-supervised-mode) through one of Apple's [Automated Device Enrollment (ADE)](https://deploy.apple.com/) options. To configure an iOS update policy, see [Manage iOS/iPadOS software update policies in Intune](/intune/intune-service/protect/software-updates-ios).

#### Encrypt devices

Use the following platform-specific options to encrypt corporate data at rest on devices: 

- **MacOS** - To configure full-disk encryption on macOS, [use FileVault disk encryption for macOS with Intune](/intune/intune-service/protect/encrypt-devices-filevault).

- **Windows** – For Windows devices, [manage disk encryption policy for Windows devices with Intune](/intune/intune-service/protect/encrypt-devices). Intune policy can enforce BitLocker for volumes and disks, and Personal Data Encryption that provides file-based data encryption capabilities linked to a user’s credentials. 

#### Protect corporate data at the app-level with application protection policies  

To keep your corporate data secure within managed apps, use Intune app protection policies. [Intune app protection policies](/intune/intune-service/apps/app-protection-policy) help safeguard your organization's data by controlling how it is accessed and shared. For instance, these policies can block users from copying and pasting corporate data into personal apps or require a PIN to access corporate email.

To get started creating and using these policies, see [How to create and assign app protection policies](/intune/intune-service/apps/app-protection-policies). For some examples of three increasing levels of security configurations you can use, see Intune’s [data protection framework](/intune/intune-service/apps/app-protection-framework) for app protection policy.

### 4. Monitor device risk with endpoint threat detection

Once you've accomplished the first three objectives, configure endpoint security on devices and begin monitoring for emerging threats so you can remediate them before they become a larger problem.

The following are a few of the Microsoft solutions you can use and combine:

- **Microsoft Defender with Microsoft Intune** - When you [integrate Microsoft Defender for Endpoint with Intune](/intune/intune-service/protect/advanced-threat-protection-configure), you can use the Intune admin center to configure Defender for Endpoint on devices managed by Intune, view threat data and recommendations from Defender, and then act to remediate those issues. You can also use the [*Defender for Endpoint security settings management*](/intune/intune-service/protect/mde-security-integration) scenario that allows use of Intune policy to manage configurations for Defender on devices that aren’t enrolled with Intune.

- **Microsoft Sentinel** –  [Microsoft Sentinel](/azure/sentinel/overview) is a cloud-native security information and event management (SIEM) solution that helps you uncover and quickly respond to sophisticated threats.

With the [Intune Data warehouse](/intune/intune-service/developer/reports-nav-create-intune-reports), you can send device and app management data to reporting tools for intelligent filtering of alerts to reduce noise.  Options include but are not limited to [connecting to the Data Warehouse with Power BI](/intune/intune-service/developer/reports-proc-get-a-link-powerbi) and use of SIEM solutions through use of a [OData custom client](/intune/intune-service/developer/reports-nav-intune-data-warehouse#odata-custom-client).

## Zero Trust and your OT networks

[Microsoft Defender for IoT](/azure/defender-for-iot/organizations/) is a unified security solution built specifically to identify devices, vulnerabilities, and threats across IoT and operational technology (OT) networks. Use Defender for IoT to apply security across your entire IoT/OT environment, including existing devices that might not have built-in security agents.

OT networks often differ from traditional IT infrastructure and need a specialized approach to Zero Trust. OT systems use unique technology with proprietary protocols and can include aging platforms with limited connectivity and power, specific safety requirements, and unique exposures to physical attacks.

Defender for IoT supports Zero Trust principles by addressing OT-specific challenges, like:

- Helping you control remote connections into your OT systems.
- Reviewing and helping you reduce interconnections between dependent systems.
- Finding single points of failure in your network.

Deploy Defender for IoT network sensors to detect devices and traffic and watch for OT-specific vulnerabilities. Segment your sensors into sites and zones across your network to monitor traffic between zones, and follow Defender for IoT's risk-based mitigation steps to lower risk across your OT environment. Defender for IoT then continuously monitors your devices for anomalous or unauthorized behavior.

:::image type="content" source="../media/integrate/endpoints/defender-for-iot.png" alt-text="Diagram of Defender for IoT deployed in an OT network." border="false":::

Integrate with Microsoft services, such as [Microsoft Sentinel](/azure/defender-for-iot/organizations/iot-advanced-threat-monitoring) and other partner services, including both SIEM and ticketing systems, to share Defender for IoT data across your organization.

For more information, see:

- [Zero Trust and your OT networks](/azure/defender-for-iot/organizations/concept-zero-trust)
- [Monitor your OT networks with Zero Trust principles](/azure/defender-for-iot/organizations/monitor-zero-trust)
- [Investigate Defender for IoT incidents with Microsoft Sentinel](/azure/defender-for-iot/organizations/iot-advanced-threat-monitoring)

## Products covered in this guide

**Microsoft Azure**

[Microsoft Entra ID](https://azure.microsoft.com/products/active-directory/)

[Microsoft Sentinel](https://azure.microsoft.com/pricing/details/microsoft-sentinel)

**Microsoft 365**

[Microsoft Intune](https://www.microsoft.com/security/business/endpoint-management/microsoft-intune)

[Microsoft Defender for Endpoint](https://www.microsoft.com/security/business/threat-protection/endpoint-defender)

[Microsoft Defender for IoT](/defender-for-iot/get-started)

[Microsoft Intune](https://www.microsoft.com/security/business/endpoint-management/microsoft-intune)

## Conclusion

A Zero Trust approach can significantly strengthen the security posture of your devices and endpoints. For further information or help with implementation, please contact your Customer Success team, or continue to read through the other chapters of this guide that spans all Zero Trust pillars.

Learn more about implementing an end-to-end Zero Trust strategy for:

- [Identity](https://aka.ms/ZTIdentity)
- [Data](https://aka.ms/ZTData)

[!INCLUDE [navbar, bottom](../includes/navbar-bottom.md)]
