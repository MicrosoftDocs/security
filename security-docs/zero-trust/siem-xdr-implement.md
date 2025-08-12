---
title: Zero Trust Security with Microsoft Sentinel and Defender XDR
description: Transform your security posture with Microsoft Sentinel and Defender XDR. Benefit from AI-powered threat detection and incident response for Zero Trust.
author: batamig
ms.author: bagol
ms.subservice: zero-trust
manager: raynemw
ms.date: 02/05/2025
ms.topic: how-to
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

#customerIntent: As a security analyst, I want to use Microsoft Sentinel and Defender XDR for incident response so that I can effectively detect and mitigate threats under a Zero Trust model.
---

# Zero Trust security with Microsoft Sentinel and Defender XDR

Microsoft Defender XDR is an XDR solution that complements Microsoft Sentinel. An XDR pulls raw telemetry data from multiple services like cloud applications, email security, identity, and access management.

Using artificial intelligence (AI) and machine learning, the XDR performs automatic analysis, investigation, and real-time response. It also correlates security alerts into larger incidents, giving security teams greater visibility into attacks and prioritizing incidents to help analysts gauge threat risk levels.

With Microsoft Sentinel, you can connect to many security sources using built-in connectors and industry standards. With its AI, you can correlate multiple low-fidelity signals spanning multiple sources to create a complete view of the ransomware kill chain and prioritized alerts.

## Common attack order

This section covers a typical attack scenario involving a phishing attack and how to respond to the incident with Microsoft Sentinel and Microsoft Defender XDR.

:::image type="content" source="./media/common-attack-defense.svg" alt-text="Diagram of a common attack scenario and defenses provided by Microsoft security products." lightbox="./media/common-attack-defense.svg" border="false":::

The diagram shows the Microsoft security products that detect each attack step and how attack signals and SIEM data flow to Microsoft Defender XDR and Microsoft Sentinel.

Here's a summary of the attack.

| Attack step | Detection service and signal source | Defenses in place |
| --- | --- | --- |
| 1. Attacker sends phishing email  | Microsoft Defender for Office 365 | Protects mailboxes with advanced anti-phishing features that can protect against malicious impersonation-based phishing attacks. |
| 2. User opens attachment | Microsoft Defender for Office 365 | The Microsoft Defender for Office 365 Safe Attachments feature opens attachments in an isolated environment for more threat scanning (detonation). |
| 3. Attachment installs malware | Microsoft Defender for Endpoint | Protects endpoints from malware with its next generation protection features, such as cloud-delivered protection and behavior-based/heuristic/real-time antivirus protection. |
| 4. Malware steals user credentials | Microsoft Entra ID and Microsoft Entra ID Protection | Protects identities by monitoring user behavior and activities, detecting lateral movement, and alerting on anomalous activity. |
| 5. Attacker moves laterally across Microsoft 365 apps and data | Microsoft Defender for Cloud Apps | Can detect anomalous activity of users accessing cloud apps. |
| 6. Attacker downloads sensitive files from a SharePoint folder | Microsoft Defender for Cloud Apps | Can detect and respond to mass download events of files from SharePoint. |

If you onboarded your Microsoft Sentinel workspace to the Defender portal, SIEM data is available with Microsoft Sentinel directly in the Microsoft Defender portal.

## Incident response using Microsoft Sentinel and Microsoft Defender XDR

After observing a common attack, use Microsoft Sentinel and Microsoft Defender XDR for incident response.

Select the relevant tab for your workspace depending on whether you onboarded it to the Defender portal.

## [Defender portal](#tab/defender-portal)

After onboarding Microsoft Sentinel to the Defender portal, complete all incident response steps directly in the Microsoft Defender portal just as you do for other Microsoft Defender XDR incidents. Supported steps include everything from triage to investigation and resolution.

Use the Microsoft Sentinel area in the Microsoft Defender portal for features that aren't available with the Defender portal alone.

For more information, see [Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR](respond-incident-defender.md).

## [Azure portal](#tab/azure-portal)

Use the following high-level process to respond to an incident with Microsoft Sentinel in the Azure portal together with Microsoft Defender XDR:

1. Triage the incident in the Microsoft Sentinel portal.
1. Move to the Microsoft Defender portal to start your investigation.
1. If needed, continue the investigation in the Microsoft Sentinel portal.
1. Resolve the incident in the Microsoft Sentinel portal.

The following diagram shows the process, starting with discovery and triage in Microsoft Sentinel.

:::image type="content" source="./media/investigation-flow.svg" alt-text="Diagram of performing incident investigation using Microsoft Sentinel and Microsoft Defender XDR." lightbox="./media/investigation-flow.svg":::

For more information, see [Respond to an incident using Microsoft Sentinel and Microsoft Defender XDR](respond-incident-azure.md).

---

## Related content

For more information, see [Incident response with integrated SIEM and XDR](siem-xdr-overview.md).

## [Defender portal](#tab/defender-portal)

For more information about applying Zero Trust principles in Microsoft 365, see:

- [Zero Trust deployment plan with Microsoft 365](/microsoft-365/security/microsoft-365-zero-trust?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)
- [Deploy your identity infrastructure for Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)
- [Zero Trust identity and device access configurations](zero-trust-identity-device-access-policies-overview.md)
- [Manage devices with Microsoft Intune](/microsoft-365/solutions/manage-devices-with-intune-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)
- [Pilot and deploy Microsoft Defender XDR](/defender-xdr/pilot-deploy-overview?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)
- [Manage data privacy and data protection with Microsoft Priva and Microsoft Purview](/microsoft-365/solutions/data-privacy-protection?bc=/security/zero-trust/breadcrumb/toc.json&toc=/security/zero-trust/toc.json)
- [Integrate SaaS apps for Zero Trust with Microsoft 365](integrate-saas-apps.md)

## [Azure portal](#tab/azure-portal)

For more information, see [Recommended training for SIEM and XDR](siem-xdr-training.md).

For more information about applying Zero Trust principles to Azure, see:

- [Azure IaaS overview](/security/zero-trust/azure-infrastructure-overview)
- [Azure storage](/security/zero-trust/azure-infrastructure-storage)
- [Virtual machines](/security/zero-trust/azure-infrastructure-virtual-machines)
- [Spoke virtual networks](/security/zero-trust//azure-infrastructure-iaas)
- [Hub virtual networks](/security/zero-trust//azure-infrastructure-networking)
- [Spoke virtual network with Azure PaaS Services](/security/zero-trust/azure-infrastructure-paas)
- [Azure Virtual Desktop](/security/zero-trust/azure-infrastructure-avd)
- [Azure Virtual WAN](/security/zero-trust/azure-virtual-wan)
- [IaaS applications in Amazon Web Services](/security/zero-trust/secure-iaas-apps)

---