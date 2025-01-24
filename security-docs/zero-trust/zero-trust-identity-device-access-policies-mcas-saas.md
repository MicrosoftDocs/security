---
title: Recommended Microsoft Defender for Cloud Apps policies for SaaS apps
description: Describes recommended policies for integration with Microsoft Defender for Cloud Apps.
author: BrendaCarter
manager: dansimp
ms.topic: conceptual
audience: Admin
ms.author: bcarter
ms.date: 01/23/2025
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- m365-security
- zerotrust-solution
- tier2
ms.service: microsoft-365-zero-trust
search.appverid: met150
---

# Recommended Microsoft Defender for Cloud Apps policies for SaaS apps

Microsoft Defender for Cloud Apps builds on Microsoft Entra Conditional Access policies to enable real-time monitoring and control of granular actions with SaaS apps, such as blocking downloads, uploads, copy and paste, and printing. This feature adds security to sessions that carry inherent risk, such as when corporate resources are accessed from unmanaged devices or by guests.

Defender for Cloud Apps also integrates natively with Microsoft Purview Information Protection, providing real-time content inspection to find sensitive data based on sensitive information types and sensitivity labels and to take appropriate action.

This guidance includes recommendations for these scenarios:

- Bring SaaS apps into IT management
- Tune protection for specific SaaS apps
- Configure Microsoft Purview Data Loss Prevention (DLP) to help comply with data protection regulations

## Bring SaaS apps into IT management

The first step in using Defender for Cloud Apps to manage SaaS apps is to discover these apps and then add them to your Microsoft Entra organization. If you need help with discovery, see [Discover and manage SaaS apps in your network](/cloud-app-security/tutorial-shadow-it). After you discover the apps, [add them to your Microsoft Entra organization](/entra/identity/enterprise-apps/add-application-portal).

You can begin to manage these apps by doing the following steps:

1. In Microsoft Entra ID, create a new Conditional Access policy and configure it to use [Conditional Access App Control](/defender-cloud-apps/proxy-intro-aad). This configuration redirects the request to Defender for Cloud Apps. You can create one policy and add all SaaS apps to this policy.
1. In Defender for Cloud Apps, create session policies. Create one policy for each control you want to apply.

Permissions to SaaS apps are typically based on business need for access to the app. These permissions can be highly dynamic. Using Defender for Cloud Apps policies ensures protection to app data, regardless of whether users are assigned to a Microsoft Entra group associated with starting point, enterprise, or specialized security protection.

To protect data across your collection of SaaS apps, the following diagram illustrates the necessary Microsoft Entra Conditional Access policy plus suggested policies you can create in Defender for Cloud Apps. In this example, the policies created in Defender for Cloud Apps apply to all SaaS apps you're managing. These policies are designed to apply appropriate controls based on whether devices are managed as well as sensitivity labels that are already applied to files.

:::image type="content" source="media/microsoft-365-policies-configurations/manage-saas-apps-2.svg" alt-text="Diagram that shows the policies for managing SaaS apps in Defender for Cloud Apps." lightbox="media/microsoft-365-policies-configurations/manage-saas-apps-2.svg":::

The following table lists the new Conditional Access policy you must create in Microsoft Entra ID:

|Protection level|Policy|More information|
|---|---|---|
|All protection levels|[Use Conditional Access App Control in Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Configures your IdP (Microsoft Entra ID) to work with Defender for Cloud Apps.|

This next table lists the example policies from the previous table that you can create to protect all SaaS apps. Be sure to evaluate your business, security, and compliance objectives and then create policies that provide the most appropriate protection for your environment.

|Protection level|Policy|
|---|---|
|Starting point|Monitor traffic from unmanaged devices <br/><br/> Add protection to file downloads from unmanaged devices|
|Enterprise|Block download of files labeled with sensitive or classified from unmanaged devices (results in browser only access)|
|Specialized security|Block download of files labeled with classified from all devices (results in browser only access)|

For end-to-end instructions for setting up Conditional Access App Control, see [Deploy Conditional Access App Control for featured apps](/cloud-app-security/proxy-deployment-aad). This article walks you through the process of creating the necessary conditional access policy in Microsoft Entra ID and testing your SaaS apps.

For more information, see [Protect apps with Microsoft Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/proxy-intro-aad).

## Tune protection for specific SaaS apps

You might want to apply other monitoring and controls to specific SaaS apps, which you can do in Defender for Cloud Apps. For example, if your organization heavily uses the Box, it makes sense to apply more controls. Or, if your legal or finance department is using a specific SaaS app for sensitive business data, you can target extra protection for these apps.

For example, you can protect your Box environment with the following types of [built-in anomaly detection policy templates](/defender-cloud-apps/anomaly-detection-policy#anomaly-detection-policies):

- Activity from anonymous IP addresses
- Activity from infrequent country/region
- Activity from suspicious IP addresses
- Impossible travel
- Activity performed by terminated user (requires Microsoft Entra ID as IdP)
- Malware detection
- Multiple failed login attempts
- Ransomware activity
- Risky OAuth App
- Unusual file share activity

Anomaly detection policy templates are added regularly. For examples of how to apply more protection to specific apps, see [Protecting connected apps](/cloud-app-security/protect-connected-apps).

[How Defender for Cloud Apps helps protect your Box environment](/cloud-app-security/protect-box) demonstrates the types of controls that can help you protect your business data in Box and other apps with sensitive data.

## Configure DLP to help comply with data protection regulations

Defender for Cloud Apps can be a valuable tool for configuring protection for compliance regulations. You create specific policies to look for regulated data and configure each policy to take appropriate action.

The following illustration and table provide several examples of policies that you can configure to help comply with the General Data Protection Regulation (GDPR). Based on the sensitivity of the data, each policy is configured to take appropriate action.

:::image type="content" source="media/microsoft-365-policies-configurations/microsoft-cloud-app-security-data-loss-prevention.svg" alt-text="Diagram that shows the Defender for Cloud Apps policies for data loss prevention page." lightbox="media/microsoft-365-policies-configurations/microsoft-cloud-app-security-data-loss-prevention.svg":::

|Protection level|Example policies|
|---|---|
|Starting point|Alert when files containing the **Credit Card Number** sensitive information type are shared outside the organization. <br/><br/> Block downloads of files containing the **Credit Card Number** sensitive information type to unmanaged devices.|
|Enterprise|Protect downloads of files containing the **Credit Card Number** sensitive information type to managed devices. <br/><br/> Block downloads of files containing the **Credit Card Number** sensitive information type to unmanaged devices. <br/><br/> Alert when a file with one of these labels is uploaded to OneDrive or Box: **Customer data**, **Human Resources: Salary Data**, or **Human Resources, Employee data**.|
|Specialized security|Alert when files with the **Highly classified** label are downloaded to managed devices. <br/><br/> Block downloads of files with the **Highly classified** label to unmanaged devices.|

## Next steps

For more information about using Defender for Cloud Apps, see [Microsoft Defender for Cloud Apps documentation](/defender-cloud-apps/).
