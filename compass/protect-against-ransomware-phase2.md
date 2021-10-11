---
title: "Phase 2: Limit the scope of damage"
keywords: ransomware, human-operated ransomware, human operated ransomware, HumOR, extortion attack, ransomware attack, encryption, cryptovirology, extortionware, malicious encryption
ms.author: josephd
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection: 
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-ransomware
- m365solution-overview
ms.custom: 
description: Deploy ransomware protection to limit the scope of damage of an attacker by protecting privileged roles.

---

# Phase 2: Limit the scope of damage

In this phase, you prevent attackers from obtaining a large scope of access for potential damage to data and systems by protecting privileged roles.

## Privileged access strategy

You must implement a comprehensive strategy to reduce the risk of privileged access compromise.

All other security controls can easily be invalidated by an attacker with privileged access in your environment. Ransomware attackers use privileged access as a quick path to control all critical assets in the organization for their extortion. 

### Program and project member accountabilities

This table describes a privileged access strategy against ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| CISO or CIO | | Executive sponsorship |
| Program lead | | Drive results and cross-team collaboration |
|  | IT and [Security Architects](/azure/cloud-adoption-framework/organize/cloud-security-architecture) |  Prioritize components integrate into architectures |
|  | [Identity and Key Management](/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) | Implement identity changes |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User Team | Implement changes to devices and Office 365 tenant |
|  | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  | User Education Team | Update any password guidance |
|  |  |  |

### Implementation checklist

Build a multi-part strategy using the guidance at [https://aka.ms/SPA](https://aka.ms/SPA) that includes this checklist.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> | Enforce end-to-end session security. | Explicitly validates the trust of users and devices before allowing access to administrative interfaces (using [Azure AD Conditional Access](/azure/active-directory/conditional-access/overview)). |
| <input type="checkbox" /> |  Protect and monitor identity systems. | Prevents privilege escalation attacks including directories, identity management, administrator accounts and groups, and consent grant configuration. |
| <input type="checkbox" /> | Mitigate lateral traversal. | Ensures that compromising a single device does not immediately lead to control of many or all other devices using local account passwords, service account passwords, or other secrets. |
| <input type="checkbox" /> | Ensure rapid threat response. | Limits an adversary's access and time in the environment. See [Detection and Response](protect-against-ransomware-phase2.md#detection-and-response) for more information. |
|  |  |  |


### Implementation results and timelines

Try to achieve these results in 30-90 days:

- 100 % of admins required to use secure workstations
- 100 % local workstation/server passwords randomized
- 100 % deployment of privilege escalation mitigations

## Detection and response

Your organization needs responsive detection and remediation of common attacks on endpoints, email, and identities. Minutes matter. You must rapidly remediate common attack entry points to limit the attacker’s time to laterally traverse your organization.

### Program and project member accountabilities

This table describes the improvement of your detection and response capability against ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| CISO or CIO | | Executive sponsorship |
| Program lead from [Security Operations](/azure/cloud-adoption-framework/organize/cloud-security-operations-center) | | Drive results and cross-team collaboration |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure Team | Implement client and server agents/features |
|  | [Security Operations](/azure/cloud-adoption-framework/organize/cloud-security-operations-center) | Integrate any new tools into security operations processes |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User Team | Enable features for Defender for Endpoints, Defender for Office 365, Defender for Identity, and Cloud App Security |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Identity Team | Implement Azure AD security and Defender for Identity |
|  | [Security Architects](/azure/cloud-adoption-framework/organize/cloud-security-architecture) |  Advise on configuration, standards, and tooling |
|  | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |

### Implementation checklist

Apply these best practices for improving your detection and response.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> | Prioritize common entry points: <br><br> - Use integrated Extended Detection and Response (XDR) tools like [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection) to provide high quality alerts and minimize friction and manual steps during response. <br><br> - Monitor for brute-force attempts like [password spray](/defender-for-identity/compromised-credentials-alerts). | Ransomware (and other) operators favor endpoint, email, identity, and RDP as entry points. |
| <input type="checkbox" /> | Monitor for an adversary disabling security (this is often part of an attack chain), such as: <br><br> - Event log clearing, especially the Security Event log and PowerShell Operational logs. <br><br> - Disabling of security tools and controls (associated with some groups). | Attackers target security detection facilities to more safely continue their attack. |
| <input type="checkbox" /> | Don’t ignore commodity malware. | Ransomware attackers regularly purchase access to target organizations from dark markets. |
| <input type="checkbox" /> | Integrate outside experts into processes to supplement expertise, such as the [Microsoft Detection and Response Team (DART)](https://aka.ms/dart). | Experience counts for detection and recovery. |
| <input type="checkbox" /> | Rapidly isolate compromised computers using [Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network). | Windows 10 integration makes this easy. |
|  |  |  |


## Next step

[![Phase 3. Make it hard to get in](media/protect-against-ransomware/protect-against-ransomware-phase3.png)](protect-against-ransomware-phase3.md)

Continue with [Phase 3](protect-against-ransomware-phase3.md) to make it hard for an attacker to get into your environment by incrementally removing risks.

## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](human-operated-ransomware.md)
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [The latest Microsoft Security Intelligence Report](https://www.microsoft.com/securityinsights/) (see pages 22-24)
- **Ransomware: A pervasive and ongoing threat** report in the **Threat analytics** node of the Microsoft 365 Defender portal (see these [licensing requirements](/microsoft-365/security/defender/prerequisites#licensing-requirements))

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)

Microsoft 365 Defender:

- [Find ransomware with advanced hunting](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](backup-plan-to-protect-against-ransomware.md)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Azure Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Cloud App Security:

-  [Create anomaly detection policies in Cloud App Security](/cloud-app-security/anomaly-detection-policy)

Microsoft Security team blog posts:

- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Becoming resilient by understanding cybersecurity risks: Part 4—navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response—to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)

