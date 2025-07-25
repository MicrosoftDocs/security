---
title: "Limit the impact that ransomware attacks can have"
ms.author: kenwith
author: kenwith
ms.date: 10/16/2024
f1.keywords:
- NOCSH
manager: dougeby
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.collection: 
- msftsolution-ransomware
ms.custom: cx-rw
description: How to prevent ransomware attacks by protecting privileged roles in your organization and limiting the scope of damage a cybercriminal attacker can do.

---

# Limit the impact of ransomware attacks

The next step to limit the impact of ransomware attacks is to *protect privileged roles* -- the kind of jobs where people handle a lot of privileged information in an organization. 

This phase of ransomware prevention aims to prevent threat actors from getting a lot of access to your systems.

The more access a cybercriminal has to your organization and devices, the higher the potential damage to your data and systems.

> [!IMPORTANT]
> **Read ransomware prevention series, and make your organization hard to cyber attack.**
>
>- [Have a recovery plan](protect-against-ransomware-phase1.md)
>- [A plan to limit the harm done](protect-against-ransomware-phase2.md)
>- [Make it hard to get in](protect-against-ransomware-phase3.md)


## Create a ransomware privileged access strategy

You must apply a thorough and comprehensive strategy to reduce the risk of privileged access compromise.

Any other security control you apply can easily be invalidated by a threat actor with privileged access in your environment. Malicious actors can gain access using social engineering and even leverage AI to generate and render malicious code and URLs. Ransomware threat actors use privileged access as a quick path to control all critical assets in the organization for attack and subsequent extortion. 

### Who is accountable in the program or project

This table describes a privileged access strategy to prevent ransomware in terms of a sponsorship/program management/project management hierarchy to drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| CISO or CIO | | Executive sponsorship |
| Program lead | | Drive results and cross-team collaboration |
|  | IT and [Security Architects](/azure/cloud-adoption-framework/organize/cloud-security-architecture) | Prioritize components integrate into architectures |
|  | [Identity and Key Management](/azure/cloud-adoption-framework/organize/cloud-security-identity-keys) | Implement identity changes |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User Team | Implement changes to devices and Office 365 tenant |
|  | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  | User Education Team | Update any password guidance |
|  |  |  |

### Ransomware privileged access strategy checklist

Build a multi-part strategy using the guidance at [https://aka.ms/SPA](https://aka.ms/SPA) that includes this checklist.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> |Enforce end-to-end session security. |Explicitly validates the trust of users and devices before allowing access to administrative interfaces (using [Microsoft Entra Conditional Access](/azure/active-directory/conditional-access/overview)). |
| <input type="checkbox" /> |Protect and monitor identity systems. |Prevents privilege escalation attacks including directories, identity management, administrator accounts and groups, and consent grant configuration. |
| <input type="checkbox" /> |Mitigate lateral traversal. |Ensures that compromising a single device does not immediately lead to control of many or all other devices using local account passwords, service account passwords, or other secrets. |
| <input type="checkbox" /> |Ensure rapid threat response. |Limits an adversary's access and time in the environment. See [Detection and Response](protect-against-ransomware-phase2.md#ransomware-detection-and-response) for more information. |
|  |  |  |


### Implementation results and timelines

Try to achieve these results in 30-90 days:

- 100% of admins are required to use secure workstations

- 100% local workstation/server passwords are randomized

- 100% privilege escalation mitigations are deployed

## Ransomware detection and response

Your organization needs responsive detection and remediation of common attacks on endpoints, email, and identities. Minutes matter.

You must quickly remediate common attack entry points to limit the threat actor's time to laterally traverse your organization.

###  Who is accountable in the program or project

This table describes the improvement of your detection and response capability against ransomware in terms of a sponsorship/program management/project management hierarchy to determine and drive results.

| Lead | Implementor | Accountability |
|:-------|:-------|:-----|
| CISO or CIO | | Executive sponsorship |
| Program lead from [Security Operations](/azure/cloud-adoption-framework/organize/cloud-security-operations-center) | | Drive results and cross-team collaboration |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Infrastructure Team | Implement client and server agents/features |
|  | [Security Operations](/azure/cloud-adoption-framework/organize/cloud-security-operations-center) | Integrate any new tools into security operations processes |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Productivity / End User Team | Enable features for Defender for Endpoint, Defender for Office 365, Defender for Identity, and Defender for Cloud Apps |
|  | [Central IT](/azure/cloud-adoption-framework/organize/central-it) Identity Team | Implement Microsoft Entra security and Defender for Identity |
|  | [Security Architects](/azure/cloud-adoption-framework/organize/cloud-security-architecture) | Advise on configuration, standards, and tooling |
|  | [Security Policy and Standards](/azure/cloud-adoption-framework/organize/cloud-security-policy-standards) | Update standards and policy documents |
|  | [Security Compliance Management](/azure/cloud-adoption-framework/organize/cloud-security-compliance-management) | Monitor to ensure compliance |
|  |  |  |

### Ransomware detection and response checklist

Apply these best practices for improving your detection and response.

| Done| Task | Description |
|:-------|:-------|:-----|
| <input type="checkbox" /> | Prioritize common entry points: <br><br> - Use integrated Extended Detection and Response (XDR) tools like [Microsoft Defender XDR](/microsoft-365/security/mtp/microsoft-threat-protection) to provide high quality alerts and minimize friction and manual steps during response. <br><br> - Monitor for brute-force attempts like [password spray](/defender-for-identity/compromised-credentials-alerts). |Ransomware (and other) operators favor endpoint, email, identity, and RDP as entry points. |
| <input type="checkbox" /> | Monitor for an adversary disabling security (this is often part of an attack chain), such as: <br><br> - Event log clearing, especially the Security Event log and PowerShell Operational logs. <br><br> - Disabling of security tools and controls. |Threat actors target security detection facilities to continue their attack more safely. |
| <input type="checkbox" /> | Don’t ignore commodity malware. |Ransomware threat actors regularly purchase access to target organizations from dark markets. |
| <input type="checkbox" /> | Integrate outside experts into processes to supplement expertise, such as the [Microsoft Detection and Response Team (DART)](https://aka.ms/dart). | Experience counts for detection and recovery. |
| <input type="checkbox" /> | Use [Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network) to rapidly isolate impacted devices.|Windows 11 and 10 integration makes this easy. |
|  |  |  |


## Next step

[![Phase 3. Make it hard to get in](media/protect-against-ransomware/protect-against-ransomware-phase3.png)](protect-against-ransomware-phase3.md)

Continue with [Phase 3](protect-against-ransomware-phase3.md) to make it hard for a threat actor to get into your environment by incrementally removing risks.

## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](human-operated-ransomware.md)
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (see pages 10-19)
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft Defender portal
- Microsoft's Detection and Response Team (DART) ransomware [approach](/security/operations/incident-response-playbook-dart-ransomware-approach) and [case study](dart-ransomware-case-study.md)

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Threat analytics reports for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) in the Microsoft Defender portal

Microsoft Defender XDR:

- [Find ransomware with advanced hunting](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](/azure/security/fundamentals/backup-plan-to-protect-against-ransomware)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

- [Create anomaly detection policies in Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Microsoft Security team blog posts on ransomware mitigation guidance:

- [Defending against human-operated ransomware attacks with Microsoft Copilot for Security (March 2024)](https://www.microsoft.com/en-us/security/blog/2024/03/04/defend-against-human-operated-ransomware-attacks-with-microsoft-copilot-for-security/)
- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [A guide to combatting human-operated ransomware: Part 1 (September 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Key steps on how Microsoft's Detection and Response Team (DART) conducts ransomware incident investigations.

- [A guide to combatting human-operated ransomware: Part 2 (September 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Recommendations and best practices.

- [Becoming resilient by understanding cybersecurity risks: Part 4—navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response—to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
