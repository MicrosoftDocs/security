---
title: Incident Response with Integrated SIEM and XDR
description: Learn how to use Microsoft Sentinel with Microsoft Defender XDR and Microsoft Defender for Cloud, an XDR solution for Zero Trust.
author: batamig
ms.author: bagol
manager: raynemw
ms.date: 02/05/2025
ms.topic: concept-article
ms.service: microsoft-365-zero-trust
ms.collection: 
  - zerotrust-solution
  - msftsolution-secops
  - msftsolution-overview
  - zerotrust-azure
  - usx-security
appliesto: 
    - Microsoft Sentinel in the Microsoft Defender portal
    - Microsoft Sentinel in the Azure portal
ms.localizationpriority: medium
#customer intent: As a security professional, I want to understand how to integrate SIEM and XDR solutions so that I can improve incident response and remediation.
---

<!---

Writers notes:

For updates to product names, please also update the appropriate figures.

For any updates to figures, please update the corresponding posters as needed and republish the Visio and PDF files in the Microsoft Download Center.

For new articles in this series, please add:

- Cross-links FROM all the other articles in this series TO the new article.
- A link to the Zero Trust Guidance Center page (index.yml) as needed.

--->

# Incident response with integrated SIEM and XDR

This solution guide walks through setting up Microsoft extended detection and response (XDR) tools with Microsoft Sentinel to accelerate your organization's ability to respond to and remediate cybersecurity attacks.

Microsoft Defender XDR is an XDR solution that automatically collects, correlates, and analyzes signal, threat, and alert data from across your Microsoft 365 environment.

Microsoft Sentinel is a cloud-native solution that provides security information and event management (SIEM) and security orchestration, automation, and response (SOAR) capabilities. Together, Microsoft Sentinel and Microsoft Defender XDR provide a comprehensive solution to help organizations defend against modern attacks.

This guidance helps you mature your Zero Trust architecture by mapping the principles of Zero Trust in the following ways:

| Zero Trust Principle | Met by|
|--|:--|
Verify explicitly | Microsoft Sentinel collects data from across the environment and analyzes threats and anomalies so your organization, and any automation implemented, can act based on all available and verified data points. <br><br> Microsoft Defender XDR provides extended detection and response across users, identities, devices, apps, and emails. Configure Microsoft Sentinel automation to use the risk-based signals captured by Microsoft Defender XDR to take action, such as blocking or authorizing traffic based on the level of risk. |
Use least privileged access | Microsoft Sentinel detects anomalous activity through its User Entity Behavioral Analytics (UEBA) engine. Since security scenarios can change over time, and often very quickly, Microsoft Sentinel's threat intelligence also imports data from Microsoft or third-party providers to detect new, emerging threats and provide extra context for investigations. <br><br> Microsoft Defender XDR has Microsoft Entra ID Protection, which can block users based on the level of risk with identity. Feed any related data into Microsoft Sentinel for further analysis and automation.|
Assume breach | Microsoft Defender XDR continuously scans the environment for threats and vulnerabilities. Microsoft Sentinel analyzes collected data and each entity's behavioral trends to detect suspicious activity, anomalies, and multi-stage threats across the enterprise.<br><br> Both Microsoft Defender XDR and Microsoft Sentinel can implement automated remediation tasks, including automated investigations, device isolation, and data quarantine. Device risk can be used as a signal to feed into Microsoft Entra Conditional Access. |

## Microsoft Sentinel and XDR architecture

Microsoft Sentinel customers can use one of these methods to integrate Microsoft Sentinel with Microsoft Defender XDR services:

- Onboard Microsoft Sentinel to the Defender portal to integrate Microsoft Sentinel and Microsoft Defender XDR into a single, unified security operations (SecOps) platform. View Microsoft Sentinel data directly in the Microsoft Defender portal with the rest of your Defender incidents, alerts, vulnerabilities, and other security data.

- Use Microsoft Sentinel data connectors to ingest Microsoft Defender XDR service data into Microsoft Sentinel. View Microsoft Sentinel data in the Azure portal.

This guidance center provides information for both methods. If you've onboarded your workspace to the Defender portal, work in the Defender portal. If you haven't onboarded your workspace, work in the Azure portal unless otherwise indicated.

## [Defender portal](#tab/defender-portal)

The following illustration shows how Microsoft's XDR solution seamlessly integrates with Microsoft Sentinel in the Defender portal.

:::image type="content" source="./media/sentinel-xdr-unified-security-experience.png" alt-text="Diagram of a Microsoft Sentinel and Microsoft Defender XDR architecture with the SecOps operations platform." lightbox="./media/sentinel-xdr-unified-security-experience.png" border="false":::

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Sentinel provides support for multicloud environments and integrates with third-party apps and partners.
- Microsoft Sentinel data is ingested together with your organization's data into the Microsoft Defender portal.
- SecOps teams can analyze and respond to threats identified by Microsoft Sentinel and Microsoft Defender XDR in the Microsoft Defender portal.

## [Azure portal](#tab/azure-portal)

This illustration shows how Microsoft's XDR solution seamlessly integrates with Microsoft Sentinel in the Azure portal.

:::image type="content" source="./media/sentinel-xdr.png" alt-text="Diagram of the integration of Microsoft Sentinel and Microsoft XDR." lightbox="./media/sentinel-xdr.png" border="false":::

In this diagram:

- Insights from signals across your entire organization feed into Microsoft Defender XDR and Microsoft Defender for Cloud.
- Microsoft Defender XDR and Microsoft Defender for Cloud send SIEM log data through Microsoft Sentinel connectors.
- SecOps teams analyze and respond to threats identified in Microsoft Sentinel and Microsoft Defender XDR.
- Microsoft Sentinel provides support for multicloud environments and integrates with third-party apps and partners.

---


## Key capabilities

To implement a Zero Trust approach in managing incidents, use these Microsoft Sentinel and Defender XDR features. For workspaces onboarded to the Defender portal, use Microsoft Sentinel in the Defender portal.

Capability or feature | Description | Product |
:---|:---|:---|
|[Automated Investigation & Response (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations) | AIR capabilities are designed to examine alerts and take immediate action to resolve breaches. AIR capabilities significantly reduce alert volume, allowing security operations to focus on more sophisticated threats and other high-value initiatives. | Microsoft Defender XDR |
|[Advanced hunting](/microsoft-365/security/defender/advanced-hunting-overview) |Advanced hunting is a query-based threat hunting tool that lets you explore up to 30 days of raw data. You can proactively inspect events on your network to locate threat indicators and entities. The flexible access to data enables unconstrained hunting for both known and potential threats. | Microsoft Defender XDR |
|[Custom file indicators](/microsoft-365/security/defender-endpoint/indicator-file) | Prevent further propagation of an attack in your organization by banning potentially malicious files or suspected malware. | Microsoft Defender XDR |
|[Cloud discovery](/defender-cloud-apps/set-up-cloud-discovery) | Cloud Discovery analyzes traffic logs collected by Defender for Endpoint and assesses identified apps against the cloud app catalog to provide compliance and security information.| Microsoft Defender for Cloud Apps |
|[Custom network indicators](/microsoft-365/security/defender-endpoint/indicator-ip-domain)|By creating indicators for IPs and URLs or domains, you can now allow or block IPs, URLs, or domains based on your own threat intelligence. | Microsoft Defender XDR |
|[Endpoint detection and response (EDR) Block](/microsoft-365/security/defender-endpoint/edr-in-block-mode) | Provides added protection from malicious artifacts when Microsoft Defender Antivirus (MDAV) isn't the primary antivirus product and is running in passive mode. EDR in block mode works behind the scenes to remediate malicious artifacts that were detected by EDR capabilities. | Microsoft Defender XDR |
|[Device response capabilities](/microsoft-365/security/defender-endpoint/respond-machine-alerts) | Quickly respond to detected attacks by isolating devices or collecting an investigation package | Microsoft Defender XDR |
|[Live response](/microsoft-365/security/defender-endpoint/live-response) | Live response gives security operations teams instantaneous access to a device (also referred to as a machine) using a remote shell connection. This gives you the power to do in-depth investigative work and take immediate response actions to promptly contain identified threats in real time. | Microsoft Defender XDR |
|[Secure cloud applications](/azure/defender-for-cloud/defender-for-cloud-introduction#secure-cloud-applications) | A development security operations (DevSecOps) solution that unifies security management at the code level across multicloud and multiple-pipeline environments. | Microsoft Defender for Cloud |
|[Improve your security posture](/azure/defender-for-cloud/defender-for-cloud-introduction#improve-your-security-posture) | A cloud security posture management (CSPM) solution that surfaces actions that you can take to prevent breaches. | Microsoft Defender for Cloud |
|[Protect cloud workloads](/azure/defender-for-cloud/defender-for-cloud-introduction#protect-cloud-workloads) | A cloud workload protection platform (CWPP) with specific protections for servers, containers, storage, databases, and other workloads. | Microsoft Defender for Cloud |
|[User and Entity Behavioral Analytics (UEBA)](/azure/sentinel/enable-entity-behavior-analytics) |Analyzes behavior of organization entities such as users, hosts, IP addresses, and applications) | Microsoft Sentinel |
|[Fusion](/azure/sentinel/configure-fusion-rules) | A correlation engine based on scalable machine learning algorithms. Automatically detects multistage attacks&nbsp;also known as advanced persistent threats (APT)&nbsp;by identifying combinations of anomalous behaviors and suspicious activities that are observed at various stages of the kill chain. | Microsoft Sentinel |
|[Threat Intelligence](/azure/sentinel/threat-intelligence-integration) | Use Microsoft third-party providers to enrich data to provide extra context around activities, alerts, and logs in your environment. | Microsoft Sentinel |
|[Automation](/azure/sentinel/automation) | Automation rules are a way to centrally manage automation with  Microsoft Sentinel, by allowing you to define and coordinate a small set of rules that can apply across different scenarios. | Microsoft Sentinel |
|[Anomaly rules](/azure/sentinel/work-with-anomaly-rules) | Anomaly rule templates use machine learning to detect specific types of anomalous behavior. | Microsoft Sentinel  |
|[Scheduled queries](/azure/sentinel/detect-threats-custom) | Built-in rules written by Microsoft security experts that search through logs collected by Microsoft Sentinel for suspicious activity chains, known threats. | Microsoft Sentinel |
|[Near-real-time (NRT) rules](/azure/sentinel/create-nrt-rules) | NRT rules are limited set of scheduled rules, designed to run once every minute, in order to supply you with information as up-to-the-minute as possible.  | Microsoft Sentinel |
|[Hunting](/azure/sentinel/hunting) | To help security analysts look proactively for new anomalies that weren't detected by your security apps or even by your scheduled analytics rules, Microsoft Sentinel's built-in hunting queries guide you into asking the right questions to find issues in the data you already have on your network. | Microsoft Sentinel <br><br>For workspaces onboarded to the Defender portal, use the Microsoft Defender portal advanced hunting functionality. |
|[Microsoft Defender XDR Connector](/azure/sentinel/connect-microsoft-365-defender) | The Microsoft Defender XDR connector synchronizes logs and incidents to Microsoft Sentinel. | Microsoft Defender XDR and Microsoft Sentinel |
|[Data connectors](/azure/sentinel/connect-data-sources) | Allow for the ingestion of data for analysis in Microsoft Sentinel. | Microsoft Sentinel |
|[Content hub solution -Zero Trust (TIC 3.0)](/azure/sentinel/sentinel-solution) | Zero Trust (TIC 3.0) includes a workbook, analytics rules, and a playbook, which provide an automated visualization of Zero Trust principles, cross-walked to the Trust Internet Connections framework, helping organizations to monitor configurations over time. | Microsoft Sentinel  |
|[Security orchestration, automation, and response (SOAR)](/azure/sentinel/sentinel-soar-content) | Using automation rules and playbooks in response to security threats increases your SOC's effectiveness and saves you time and resources. | Microsoft Sentinel  |
|[SOC optimizations](/azure/sentinel/soc-optimization/soc-optimization-access) | Close coverage gaps against specific threats and tighten your ingestion rates against data that doesn't provide security value. | Microsoft Sentinel <br><br>For workspaces onboarded to the Defender portal, use SOC optimization in the Microsoft Defender portal. |

## What's in this solution

This solution guides you through implementing Microsoft Sentinel and XDR so your security operations team can effectively remediate incidents using a Zero Trust approach. Implementing Microsoft Sentinel and Microsoft Defender XDR for a Zero Trust approach includes the following phases:

1. Start by [piloting Microsoft Defender XDR services](/defender-xdr/pilot-deploy-overview?bc=/security/breadcrumb/toc.json&toc=/security/zero-trust/toc.json) so you can evaluate their features and capabilities before you complete the deployment across your organization.

1. Then, [plan your full SIEM and XDR deployment, including the workspace you'll use for Microsoft Sentinel](/unified-secops-platform/overview-plan?bc=/security/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)

1. [Set up your XDR tools and architect your workspace for Microsoft Sentinel](/unified-secops-platform/overview-deploy?bc=/security/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).

    In this phase, deploy the XDR services you'll be using across your environment.

    If you plan to work from the Azure portal, skip the step to [connect Microsoft Sentinel to the Microsoft Defender portal](/defender-xdr/microsoft-sentinel-onboard?bc=/security/breadcrumb/toc.json&toc=/security/zero-trust/toc.json). This step is only relevant if you want to use Microsoft Sentinel Defender portal, and is not relevant if you want to respond to incidents in the Azure portal.

1. Finally, respond to incidents as follows, depending on whether you onboarded to the Defender portal.:

    - [Respond to an incident using the Defender portal](respond-incident-defender.md).
    - [Respond to an incident using Microsoft Sentinel in the Azure portal with Microsoft Defender XDR](respond-incident-azure.md).

## Related content

For more information, see [implementing Microsoft Sentinel and Microsoft Defender XDR for Zero Trust](siem-xdr-implement.md).


## [Defender portal](#tab/defender-portal)

For more information about applying Zero Trust principles in Microsoft 365, see:

- [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).
- [Deploy your identity infrastructure for Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).
- [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md).
- [Manage devices with Microsoft Intune](/microsoft-365/solutions/manage-devices-with-intune-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).
- [Pilot and deploy Microsoft Defender XDR](/defender-xdr/pilot-deploy-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).
- [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json).
- [Integrate SaaS apps for Zero Trust with Microsoft 365](integrate-saas-apps.md).

## [Azure portal](#tab/azure-portal)

For more information, see [Recommended training for SIEM and XDR](siem-xdr-training.md).

For more information about applying Zero Trust principles to Azure, see:

- [Azure IaaS overview](/security/zero-trust/azure-infrastructure-overview)
- [Azure storage](/security/zero-trust/azure-infrastructure-storage)
- [Virtual machines](/security/zero-trust/azure-infrastructure-virtual-machines)
- [Spoke virtual networks](/security/zero-trust/azure-infrastructure-iaas)
- [Hub virtual networks](/security/zero-trust/azure-infrastructure-networking)
- [Spoke virtual network with Azure PaaS Services](/security/zero-trust/azure-infrastructure-paas)
- [Azure Virtual Desktop](/security/zero-trust/azure-infrastructure-avd)
- [Azure Virtual WAN](/security/zero-trust/azure-virtual-wan)
- [IaaS applications in Amazon Web Services](/security/zero-trust/secure-iaas-apps)

---