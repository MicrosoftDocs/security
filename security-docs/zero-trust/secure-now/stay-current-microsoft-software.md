---
title: Stay current on Microsoft software
description: Learn how to maintain currency across Windows, Microsoft 365, browsers, drivers, firmware, and other operating systems to reduce exposure to vulnerabilities.
ms.date: 04/21/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
ai-usage: ai-assisted
---

# Stay current on Microsoft software

Monthly installation of security updates (patching) is necessary but insufficient when threat actors exploit vulnerabilities in days, not weeks. Devices that lag in patching accumulate risk no update cycle can eliminate. The attack surface also extends beyond Windows to Microsoft 365, browsers, drivers, firmware, and other operating systems. As AI accelerates software vulnerability discovery, chasing Common Vulnerabilities and Exposures (CVEs) is inevitable, but staying current across the entire estate is the strongest defense.

As noted in the Exposure Management hub, you can use the following capabilities to accelerate your update assessment and deployment.

## Understand your software landscape across platforms

Before you can enforce currency, you need full visibility into what software is running, where, and what vulnerabilities exist across every OS and cloud.

- Deploy **Microsoft Defender for Endpoint** across all platforms — Onboard Windows, macOS, and Linux endpoints to gain unified visibility into installed software, OS versions, and active threats. For more information, see [Onboard devices to Microsoft Defender for Endpoint](https://learn.microsoft.com/defender-endpoint/onboard-configure).
- Use **Microsoft Defender Vulnerability Management** software inventory — Get a near real-time view of all installed software, versions, known CVEs, and active threat campaigns across your device fleet, regardless of operating system. For more information, see [Software inventory](https://learn.microsoft.com/defender-vulnerability-management/tvm-software-inventory).
- Enforce device compliance with **Microsoft Intune** — Create compliance policies across Windows, macOS, Linux, iOS, and Android to enforce minimum OS versions, encryption, and threat defense signals. Integrate with Conditional Access to block non-compliant devices. For more information, see [Device compliance policies in Microsoft Intune](https://learn.microsoft.com/mem/intune/protect/device-compliance-get-started).

## Deploy fast updates at scale with Windows Autopatch

**Windows Autopatch** rolls out updates through predefined deployment rings, allowing you to validate changes in groups before broad rollout. This capability shifts IT focus to policy and exceptions while Autopatch handles timing and sequencing. When critical vulnerabilities arise, expedited rollouts reduce time-to-secure, especially as AI shortens the gap between disclosure and exploitation. Autopatch update readiness also helps admins quickly pinpoint and resolve what's blocking devices from being deployment-ready. For more information, see [What is Windows Autopatch?](https://learn.microsoft.com/windows/deployment/windows-autopatch/overview/windows-autopatch-overview).

## Secure devices without requiring reboots for eligible security updates using Hotpatch

**Hotpatch** applies supported security fixes directly to running processes with no reboot required for eligible monthly updates. Eligible Windows 11 Enterprise devices are protected the moment the patch arrives, and updates that require a restart are reduced to just a few baseline updates per year. This means faster security response with less user disruption, eliminating the exposure gap that typically persists while users delay restarts. For more information, see [Hotpatch updates](https://learn.microsoft.com/windows/deployment/updates/hotpatch-enterprise).

## Extend to cloud and hybrid workloads

- Tenant-attach **Configuration Manager** for server management — Organizations already managing servers through Configuration Manager can extend that investment by enabling tenant attach, bringing those endpoints into the Microsoft Intune admin center for cloud-powered insights, actions, and policy without requiring a full migration.
  - [Configure tenant attach to support endpoint security policies from Intune](https://learn.microsoft.com/mem/intune/protect/tenant-attach-intune)
- Onboard non-Azure servers with **Azure Arc** — Bring Amazon Web Services (AWS), Google Cloud Platform (GCP), and on-premises servers into Azure's management plane for centralized policy, patching, and monitoring. For more information, see:
  - [Azure Arc overview](https://learn.microsoft.com/azure/azure-arc/overview)
  - Onboard VMs to Azure Arc through the multicloud connector <!-- TODO: link Onboard VMs to Azure Arc through the multicloud connector -->
- Scan cloud servers with **Microsoft Defender for Cloud** — Use Microsoft Defender for Servers to run vulnerability assessments across Azure, AWS, and GCP workloads with risk-based prioritization. For more information, see:
  - Configure vulnerability scanning for machines <!-- TODO: link Configure vulnerability scanning for machines -->
  - [Connect AWS accounts to Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/quickstart-onboard-aws)
  - [Connect your GCP project to Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/quickstart-onboard-gcp)

## Keep compliance and update policies aligned and enforceable

- Pair Intune compliance policies with **Microsoft Entra** Conditional Access to restrict access from devices that are outdated or carry risks from apps, drivers, or firmware. Use Intune remediation scripts to detect and resolve common update blockers automatically, before they delay compliance. As the threat landscape evolves, regularly review these policies to ensure they stay current and work together. For more information, see:
  - [Use compliance policies to set rules for devices you manage with Intune](https://learn.microsoft.com/mem/intune/protect/device-compliance-get-started)
  - [Remediations](https://learn.microsoft.com/mem/intune/fundamentals/remediations)
- Microsoft Defender for Cloud helps organizations streamline compliance with various regulatory standards by providing continuous monitoring, assessment, and remediation capabilities. For more information, see [Regulatory compliance standards in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/concept-regulatory-compliance-standards).

## Keep Microsoft 365 apps current

The **Microsoft 365 Apps admin center** shows update status by channel, making it easy to spot devices missing security updates. When faster response is needed, admins can force rapid Microsoft 365 app updates through Intune by removing download and install delays, enforcing automatic updates from the Office Content Delivery Network (CDN), and targeting specific versions. Zero day deadlines further minimize the gap between update availability and enforcement. Where possible, use capabilities like Intune Enterprise App Management to reduce overhead of keeping your apps up to date. For more information, see:

- [Set the Microsoft 365 apps update channel using the Microsoft Intune settings catalog](https://learn.microsoft.com/deployoffice/updates/change-update-channels)
- [Microsoft Intune Enterprise Application Management](https://learn.microsoft.com/mem/intune/apps/apps-enterprise-app-management)

## Deploy endpoint security policies

Deploy endpoint security policies for antivirus, firewall, disk encryption, endpoint detection and response (EDR) onboarding, attack surface reduction rules, application control, and LAPS.

- [Strengthen your security posture with Microsoft Defender XDR](https://learn.microsoft.com/defender-xdr/microsoft-365-security-center-defender-cloud)

## Migrate to cloud-joined and managed Windows devices

Migrate to cloud-joined and managed Windows devices.

- [Plan your Microsoft Entra join deployment](https://learn.microsoft.com/entra/identity/devices/device-join-plan)

## Microsoft Defender Vulnerability Management

- Asset discovery <!-- TODO: link Asset discovery -->
- Scan and remediate endpoints. <!-- TODO: link Scan and remediate end points -->

## Manage your cloud fleet

- Use **Azure Update Manager** for your server fleet specifically to schedule, assess, and deploy OS patches across Windows and Linux servers in Azure, on-premises, and multicloud environments. Azure Update Manager handles traditional patch orchestration for server workloads where coordinated maintenance windows and compliance reporting are required. For more information, see [What is Azure Update Manager?](https://learn.microsoft.com/azure/update-manager/overview).
- Identify servers missing critical updates using both Defender for Cloud and Microsoft Defender to assess devices for missing system updates and patches, surfacing recommendations that highlight which servers are outdated and prioritizing remediation by severity and exposure. For more information, see:
  - Remediate system update and patch recommendations <!-- TODO: link Remediate system update and patch recommendations -->
  - [Software inventory](https://learn.microsoft.com/defender-vulnerability-management/tvm-software-inventory)
- Onboard your servers with **Microsoft Defender for Servers** to ensure servers are visible to your security stack. Defender for Servers also provides posture management, threat protection, and EDR coverage that ensures no server is a blind spot. For more information, see [Plan Defender for Servers deployment](https://learn.microsoft.com/azure/defender-for-cloud/plan-defender-for-servers).

## Accelerate with AI-powered agents

- The **Vulnerability Remediation Agent** in Microsoft Intune is an AI-powered capability that uses data from Microsoft Defender Vulnerability Management to identify, prioritize, and provide step-by-step remediation guidance for Common Vulnerabilities and Exposures (CVEs) on managed devices, helping administrators accelerate patching and improve organizational security posture. For more information, see the Vulnerability Remediation Agent in Microsoft Intune. <!-- TODO: link Vulnerability Remediation Agent in Microsoft Intune -->
- The **Dynamic Threat Detection Agent** in Microsoft Defender is an always-on AI-driven capability in Microsoft Defender that continuously analyzes and correlates security telemetry across identities, endpoints, cloud workloads, and email to uncover hidden threats missed by traditional rules and signatures, including those exploiting unpatched or misconfigured assets. For more information, see Microsoft Security Copilot Dynamic Threat Detection Agent. <!-- TODO: link Microsoft Security Copilot Dynamic Threat Detection Agent -->

## Next steps

- [Scan and secure your source code](scan-secure-source-code.md)
- [Adopt updates for open-source software (OSS) components](adopt-open-source-updates.md)
- [Minimize internet-facing exposure](minimize-internet-exposure.md)
