---
title: "Define ransomware, human-operated ransomware, and how to prevent ransomware cyber attack"
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.service: microsoft-365-security
ms.collection:
- msftsolution-ransomware
ms.custom: cxdef-zt-ransomware
ms.topic: article
localization_priority: Normal
description: Learn what ransomware is, how it works, and how to protect against it with links to the Microsoft products that help prevent ransomware.
ms.date: 02/22/2024
---

# What is ransomware?

In practice, a *ransomware attack* blocks access to your data until a ransom is paid.

In fact, ransomware is a type of malware or phishing cyber security attack that destroys or encrypts files and folders on a computer, server, or device.

Once devices or files are locked or encrypted, cybercriminals can extort money from the business or device owner in exchange for a *key* to unlock the encrypted data. But, even when paid, cybercriminals *may never* give the key to the business or device owner, and stop access *permanently*.

> [!IMPORTANT]
> **Read ransomware prevention series, and make your organization hard to cyber attack.**
>
>- [Have a recovery plan](../security-docs/ransomware/protect-against-ransomware-phase1.md)
>- [A plan to limit the harm done](../security-docs/ransomware/protect-against-ransomware-phase2.md)
>- [Make it hard to get in](../security-docs/ransomware/protect-against-ransomware-phase3.md)

## How do ransomware attacks work?

Ransomware can be automated, or involve human hands on a keyboard -- a *human operated* attack.

### Automated ransomware attacks

*Commodity ransomware attacks* are usually automated. These cyber attacks can spread like a virus, infect devices through methods like email phishing and malware delivery, and require malware remediation.

That means one ransomware prevention technique is to safeguard your email with a system like 
[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/) that protects against malware and phishing delivery, [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/) to automatically detect and block suspicious activity on your devices, and [Microsoft Defender XDR](/microsoft-365/security/defender/) to detect malware and phishing attempts *early*.

### Human-operated ransomware attacks

*Human-operated ransomware* is the result of an **active attack** by cybercriminals that infiltrate an organization's on-premises or cloud IT infrastructure, elevate their privileges, and deploy ransomware to critical data.

These "hands-on-keyboard" attacks usually target organizations rather than a single devices.

*Human-operated* also means there is a human attacker using their insights into common system and security misconfigurations to infiltrate the organization, navigate the network, and adapt to the environment and its weaknesses as they go.

Hallmarks of these human-operated ransomware attacks typically include **credential theft** and **lateral movement** with a elevation of the privileges in stolen accounts.

Activities might take place during maintenance windows and involve security configuration gaps discovered by cybercriminals. The goal is the **deployment of a ransomware payload** to whatever *high business impact resources* the attackers choose.

> [!IMPORTANT]
> These attacks can be *catastrophic* to business operations and are difficult to clean up, requiring complete adversary eviction to protect against future attacks. Unlike commodity ransomware that usually only requires malware remediation, **human-operated ransomware will continue to threaten your business operations after the initial encounter**.

The graphic below shows how extortion-based attacks are growing in impact and likelihood.

[The impact and likelihood that human-operated ransomware attacks will continue](media/human-operated-ransomware/ransomware-extortion-based-attack.png)

## Ransomware protection for your organization

First, prevent phishing and malware delivery with [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/) to protect against malware and phishing delivery, [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/) to automatically detect and block suspicious activity on your devices, and [Microsoft Defender XDR](/microsoft-365/security/defender/) to detect to malware and phishing attempts *early*.

For a comprehensive view of ransomware and extortion and how to protect your organization, use the information in the **[Human-Operated Ransomware Mitigation Project Plan](https://download.microsoft.com/download/7/5/1/751682ca-5aae-405b-afa0-e4832138e436/RansomwareRecommendations.pptx)** PowerPoint presentation. 

Here's a summary of the guidance:

[The summary of the guidance in the Human-Operated Ransomware Mitigation Project Plan](media/human-operated-ransomware/stakes-weaknesses-plan.png)

- The stakes of ransomware and extortion-based attacks are high.
- However, the attacks have weaknesses that can reduce your likelihood of being attacked.
- There are three steps to configuring your infrastructure to exploit attack weaknesses.

For the three steps to exploit attack weaknesses, see the [Protect your organization against ransomware and extortion](protect-against-ransomware.md) solution to **quickly** configure your IT infrastructure for the best protection:

1. Prepare your organization to recover from an attack without having to pay the ransom.
2. Limit the scope of damage of a ransomware attack by protecting privileged roles.
3. Make it harder for an attacker to get into your environment by incrementally removing risks.

[![The three steps to protecting against ransomware and extortion](media/protect-against-ransomware/protect-against-ransomware-phases.png)](protect-against-ransomware.md)

Download the [Protect your organization from ransomware poster](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf) for an overview of the three phases as layers of protection against ransomware attackers.

[![The "Protect your organization from ransomware" poster](media/human-operated-ransomware/ransomware-poster-thumbnail.png)](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf)

## Additional ransomware prevention resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [2023 Microsoft Digital Defense Report](https://www.microsoft.com/security/security-insider/microsoft-digital-defense-report-2023) 
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft Defender portal
- Microsoft's Detection and Response Team (DART) ransomware [approach and best practices](/security/operations/incident-response-playbook-dart-ransomware-approach) and [case study](dart-ransomware-case-study.md)

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

Microsoft Defender for Cloud Apps:

-  [Create anomaly detection policies in Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](/azure/security/fundamentals/backup-plan-to-protect-against-ransomware)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Security team blog posts:

- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [A guide to combatting human-operated ransomware: Part 1 (September 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)
- [Automatic disruption of human-operated attacks through containment of compromised user accounts (October 2023)](https://www.microsoft.com/security/blog/2023/10/11/automatic-disruption-of-human-operated-attacks-through-containment-of-compromised-user-accounts/)
- [Ransomware as a service: Understanding the cybercrime gig economy and how to protect yourself (May 2022)](https://www.microsoft.com/security/blog/2022/05/09/ransomware-as-a-service-understanding-the-cybercrime-gig-economy-and-how-to-protect-yourself/?ocid=magicti_ta_blog)

  Key steps on how Microsoft's Detection and Response Team (DART) conducts ransomware incident investigations.

- [A guide to combatting human-operated ransomware: Part 2 (September 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)
- [Defenders beware: A case for post-ransomware investigations(October 2023)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Recommendations and best practices.

- [Becoming resilient by understanding cybersecurity risks: Part 4-navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response-to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
