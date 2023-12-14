---
title: Step 1. Set up your XDR tools - Microsoft Defender XDR and Microsoft Defender for Cloud
titleSuffix: Microsoft Defender XDR
description: Learn how to set up Microsoft Defender XDR and Microsoft Defender for Cloud, an extended detection and response (XDR) solution, and integrate it with Microsoft Sentinel.
author: mjcaparas
ms.author: macapara
manager: dansimp
ms.date: 3/29/2023
ms.topic: article
ms.service: microsoft-365-zero-trust
ms.localization_priority: Normal
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-scenario
  - zerotrust-azure
---

# Step 1. Set up your XDR tools


This article guides you to the best approaches for setting up Microsoft Defender 365 and other Microsoft XDR tools, which is the first step in setting up an integrated environment with Microsoft Sentinel.

The Microsoft Defender products are best in class for a security suite. Mature organizations unify their security platforms to ensure solutions are sharing information with each other for a more granular threat detection. Microsoft XDR tools have settings that allow the utilities to forward their information to each other. Additionally, each tool is designed to enrich data to each other.  


## Pilot and deploy Microsoft Defender XDR

Microsoft provides guidance to help you set up and get started with Microsoft Defender XDR components. The component services that are part of the Microsoft Defender XDR stack are:

- [Microsoft Defender for Identity](/defender-for-identity/what-is)
- [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security)
- [Microsoft Defender for Cloud Apps](/defender-cloud-apps/)
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint)

### Recommended order of enabling Microsoft Defender XDR components

If you haven't already set up Microsoft Defender XDR components, Microsoft recommends enabling the components in the order illustrated:

![Image of evaluate and pilot Microsoft Defender XDR](./media/m365-defender-eval-process.png) 

In the illustration: 

1. Create the evaluation environment 
2. Set up and pilot Defender for Identity 
3. Set up Defender for Office 365 
4. Set up Defender for Endpoint 
5. Set up Defender for Cloud apps 
6. Investigate and respond to threats 
7. Promote your evaluation to production 

This order is commonly recommended and designed to apply the value of the capabilities quickly based on how much effort is typically required to deploy and configure the capabilities. For example, Defender for Office 365 can be configured in less time than it takes to enroll devices in Defender for Endpoint. You should prioritize the components to meet your business needs, and can enabled in a different order. 

Use the following guidance to enable Microsoft 365 capabilities and integrate these with other components. 


|       Task  |     Description  |     See . . .  |
|:---|:---|:---|
|     Pilot and deploy Microsoft Defender XDR  |   Use this methodical process to deploy the components of Microsoft Defender XDR.  |  [Evaluate and pilot Microsoft Defender XDR](/microsoft-365/security/defender/eval-overview)  |
|     Integrate Microsoft Defender for Endpoints with Microsoft Defender for Cloud Apps  |   Defender for Cloud Apps uses the traffic information collected by Defender for Endpoint about the cloud apps and services being accessed from IT-managed devices specified in the prerequisites below. The integration doesn't require any additional deployment and can be enabled directly from the settings in Defender for Endpoint and Microsoft Defender XDR.  |   [Microsoft Defender for Endpoint integration with Microsoft Defender for Cloud Apps](/defender-cloud-apps/mde-integration)  |
|     Integrate Microsoft Defender for Identity with Defender for Cloud Apps  |   Microsoft Defender for Cloud Apps integrates with Microsoft Defender for Identity to provide user entity behavioral analytics (UEBA) across a hybrid environment - both cloud app and on-premises.  |   [Microsoft Defender for Identity integration](/defender-cloud-apps/mdi-integration) |
|     Integrate Microsoft Purview with Defender for Cloud Apps  |   Microsoft Defender for Cloud Apps lets you automatically apply sensitivity labels from Microsoft Purview Information Protection. You can then investigate files by using these labels.  |   [Microsoft Purview Information Protection integration](/defender-cloud-apps/azip-integration)  |


## Microsoft Defender portal

The [Microsoft Defender portal](https://sip.security.microsoft.com/homepage) combines protection, detection, investigation, and response to email, collaboration, identity, device, and cloud app threats, in a central place. The Microsoft Defender XDR unified portal emphasizes quick access to information, simpler layouts, and bringing related information together for easier use.

The unified portal includes:

- **[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 helps organizations secure their enterprise with a set of prevention, detection, investigation and hunting features to protect email, and Office 365 resources.
- **[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** delivers preventative protection, post-breach detection, automated investigation, and response for devices in your organization.
- **[Microsoft Defender for Identity](/defender-for-identity/what-is)** is a cloud-based security solution that leverages your on-premises Active Directory signals to identify, detect, and investigate advanced threats, compromised identities, and malicious insider actions directed at your organization.
- **[Microsoft Defender for Cloud Apps](/cloud-app-security/)** is a comprehensive cross-SaaS and PaaS solution bringing deep visibility, strong data controls, and enhanced threat protection to your cloud apps.


Watch this short video to learn about the Microsoft Defender portal.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

<a name='enable-azure-ad-identity-protection'></a>

## Enable Microsoft Entra ID Protection

Microsoft Defender XDR also ingests and includes the signals of Microsoft Entra ID Protection, as illustrated below. 


![Image of enabling Microsoft Entra ID Protection](./media/m365-azure.png)

Microsoft Entra ID Protection is licensed separately from Microsoft Defender XDR. It is included with Microsoft Entra ID P2. 

Microsoft Entra ID Protection evaluates risk data from billions of sign-in attempts and uses this data to evaluate the risk of each sign-in to your environment. This data is used by Microsoft Entra ID to allow or prevent account access, depending on how Conditional Access policies are configured.  

For this solution and target scenario, we'll also ingest the signals from Microsoft Entra ID Protection into Sentinel. To enable Microsoft Entra ID Protection, use the following resources. 

|       Task  |     Description  |     See . . .  |
|:---|:---|:---|
| Integrate Microsoft Entra ID Protection with Defender for Cloud Apps  | Microsoft Defender for Cloud Apps integrates with Microsoft Entra ID Protection to provide user entity behavioral analytics (UEBA) across a hybrid environment. | [Microsoft Entra ID Protection](/defender-cloud-apps/aadip-integration) 


## Enable Microsoft Defender for Cloud
You can complete the deployment of Microsoft XDR tools by enabling Microsoft Defender for Cloud, and then include these signals in your Sentinel workspace.  


![Image of Microsoft Defender XDR and Microsoft Defender for Cloud](./media/m365d-cloud.png)

Use the following guidance to enable Defender for Cloud and integrate capabilities.

|       Task  |     Description  |     See . . .  |
|:---|:---|:---|
|Set up Defender for Cloud |	Recommended steps to enable Microsoft Defender for Cloud and the enhanced security features | [Quickstart: Set up Microsoft Defender for Cloud](/azure/defender-for-cloud/get-started)
|Protect your server resources | With Microsoft Defender for Servers (included with Defender for Cloud), you gain access to and can deploy Microsoft Defender for Endpoint to your server resources. | [Protect your endpoints with Defender for Cloud's integrated EDR solution: Microsoft Defender for Endpoint](/azure/defender-for-cloud/integration-defender-for-endpoint?WT.mc_id=Portal-Microsoft_Azure_Security_CloudNativeCompute)

## Recommended training

### Explore security solutions in Microsoft Defender XDR

|Training  |[Explore security solutions in Microsoft Defender XDR](/training/modules/explore-security-solutions-microsoft-365-defender/)|
|---------|---------|
|:::image type="icon" source="media/generic-badge.svg" border="false"::: | This module introduces you to several features in Microsoft 365 that can help protect your organization against cyberthreats, detect when a user or computer has been compromised, and monitor your organization for suspicious activities.|
> [!div class="nextstepaction"]
> [Start >](/training/modules/explore-security-solutions-microsoft-365-defender/)

### Enable and manage Microsoft Defender for Cloud

|Training  |[Enable and manage Microsoft Defender for Cloud](/training/modules/azure-security-center/)|
|---------|---------|
|:::image type="icon" source="media/microsoft-cloud-app-security.svg" border="false"::: | Use Microsoft Defender for Cloud to strengthen security posture and protect workloads against modern threats. |
> [!div class="nextstepaction"]
> [Start >](/training/modules/azure-security-center/)


## Next steps

Continue to [Step 2](siem-workspace.md) to architect a Sentinel workspace. 


[![Image of Microsoft Sentinel and XDR solution steps with step 2 highlighted](./media/siem-xdr-solution-2.png)](siem-workspace.md)
