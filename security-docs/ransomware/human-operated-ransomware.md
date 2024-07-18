---
title: "What is ransomware?"
ms.author: sarahkatz
author: sarit1046
manager: dansimp
audience: Admin
ms.service: microsoft-365-security
ms.collection:
- msftsolution-ransomware
ms.custom: cxdef-zt-ransomware
ms.topic: article
description: Learn what ransomware is, how it works, and how to protect against it with links to the Microsoft products that help prevent ransomware.
ms.date: 02/22/2024
---

# What is ransomware?

In practice, a *ransomware attack* blocks access to your data until a ransom is paid.

In fact, ransomware is a type of malware or phishing cyber security attack that destroys or encrypts files and folders on a computer, server, or device.

Once devices or files are locked or encrypted, cybercriminals can extort money from the business or device owner in exchange for a *key* to unlock the encrypted data. But even when paid, cybercriminals *might never* give the key to the business or device owner and stop access *permanently*.

## How do ransomware attacks work?

Ransomware can be automated or involve human hands on a keyboard - a *human-operated* attack, such as seen in recent attacks using [LockBit ransomware](/security/ransomware/human-operated-ransomware). 

Human-operated ransomware attacks involve the following stages:

- Initial compromise - The threat actor first gains access to a system or environment following a period of reconnaissance to identify weaknesses in defense.

- Persistence and defense evasion - The threat actor establishes a foothold in the system or environment using a backdoor or other mechanism that operates in stealth to avoid detection by incident response teams.

- Lateral movement - The threat actor uses the initial point of entry to migrate to other systems connected to the compromised device or network environment.

- Credential access - The threat actor uses a fake sign-in page to harvest user or system credentials.

- Data theft - The threat actor steals financial or other data from compromised users or systems.

- Impact - The affected user or organization might suffer material or reputational damage.

## Common malware used in ransomware campaigns

- [Qakbot](https://www.microsoft.com/en-us/security/blog/2021/12/09/a-closer-look-at-qakbots-latest-building-blocks-and-how-to-knock-them-down/?msockid=3fd141c935036ef610d9506e34696fe7) – Uses phishing to spread malicious links, malicious attachments, or, more recently, embedded images
- [Ryuk](https://www.microsoft.com/en-us/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/?msockid=3fd141c935036ef610d9506e34696fe7) – Data encryptor typically targeting Windows 
- [Trickbot](https://www.microsoft.com/en-us/security/blog/2020/10/12/trickbot-disrupted/?msockid=3fd141c935036ef610d9506e34696fe7) – Has targeted Microsoft applications such as Excel and Word. Trickbot was typically delivered via email campaigns that used current events or financial lures to entice users to open malicious file attachments or click links to websites hosting the malicious files. Since 2022, Microsoft’s mitigation of campaigns using this malware appears to have disrupted its usefulness.

## Prevalent threat actors associated with ransomware campaigns

- [LockBit](https://techcommunity.microsoft.com/t5/microsoft-security-experts-blog/part-1-lockbit-2-0-ransomware-bugs-and-database-recovery/ba-p/3254354) – Financially motivated ransomware-as-a-service (RaaS) campaign and most prolific ransomware threat actor in the 2023-24 time period
- [Black Basta](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=Ransom:Win32/Basta&msockid=3fd141c935036ef610d9506e34696fe) – Gains access through spear-phishing emails and uses PowerShell to launch an encryption payload 

### Automated ransomware attacks

*Commodity ransomware attacks* are often automated. These cyber attacks can spread like a virus, infect devices through methods like email phishing and malware delivery, and require malware remediation.

Therefore, you can safeguard your email system using 
[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/) that protects against malware and phishing delivery. [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/) works alongside Defender for Office 365 to automatically detect and block suspicious activity on your devices, while [Microsoft Defender XDR](/microsoft-365/security/defender/) detects malware and phishing attempts *early*.

### Human-operated ransomware attacks

*Human-operated ransomware* is the result of an **active attack** by cybercriminals that infiltrate an organization's on-premises or cloud IT infrastructure, elevate their privileges, and deploy ransomware to critical data.

These "hands-on-keyboard" attacks usually target organizations rather than a single device.

*Human-operated* also means there's a human threat actor using their insights into common system and security misconfigurations. They aim to infiltrate the organization, navigate the network, and adapt to the environment and its weaknesses.

Hallmarks of these human-operated ransomware attacks typically include **credential theft** and **lateral movement** with an elevation of the privileges in stolen accounts.

Activities might take place during maintenance windows and involve security configuration gaps discovered by cybercriminals. The goal is the **deployment of a ransomware payload** to whatever *high business impact resources* the threat actors choose.

> [!IMPORTANT]
> These attacks can be *catastrophic* to business operations and are difficult to clean up, requiring complete adversary eviction to protect against future attacks. Unlike commodity ransomware that usually only requires malware remediation, **human-operated ransomware will continue to threaten your business operations after the initial encounter**.


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
1. Make it harder for a threat actor to access your environment by incrementally removing risks.

[![The three steps to protecting against ransomware and extortion](media/protect-against-ransomware/protect-against-ransomware-phases.png)](protect-against-ransomware.md)

Download the [Protect your organization from ransomware poster](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf) for an overview of the three phases as layers of protection against ransomware attacks.

[![The "Protect your organization from ransomware" poster](media/human-operated-ransomware/ransomware-poster-thumbnail.png)](https://download.microsoft.com/download/5/e/3/5e37cbff-9a7a-45b2-8b95-6d3cc5426301/protect-your-organization-from-ransomware.pdf)

## Additional ransomware prevention resources

Key information from Microsoft:

- [The latest ransomware trends from Microsoft](https://www.microsoft.com/security/blog/threat-intelligence/ransomware/), Microsoft latest ransomware blog
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [2023 Microsoft Digital Defense Report](https://www.microsoft.com/security/security-insider/microsoft-digital-defense-report-2023) 
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft Defender portal
- Microsoft Incident Response team (formerly DART) ransomware [approach and best practices](/security/operations/incident-response-playbook-dart-ransomware-approach) and [case study](dart-ransomware-case-study.md)

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Threat analytics reports for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) in the Microsoft Defender XDR portal

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
 
Microsoft Copilot for Security:

- [Defend against human-operated ransomware attacks with Microsoft Copilot for Security​​](https://www.microsoft.com/security/blog/2024/03/04/defend-against-human-operated-ransomware-attacks-with-microsoft-copilot-for-security/)

Microsoft Security ransomware mitigation resources:

See the latest list of ransomware articles in the [Microsoft Security Blog](https://www.microsoft.com/security/blog/?sort-by=relevance&date=any&s=ransomware).

- [Protect your organization against ransomware (May 2024)](/security/ransomware/protect-against-ransomware)
- [Automatic disruption of human-operated attacks through containment of compromised user accounts (October 2023)](https://www.microsoft.com/security/blog/2023/10/11/automatic-disruption-of-human-operated-attacks-through-containment-of-compromised-user-accounts/)
- [Ransomware as a service: Understanding the cybercrime gig economy and how to protect yourself (May 2022)](https://www.microsoft.com/security/blog/2022/05/09/ransomware-as-a-service-understanding-the-cybercrime-gig-economy-and-how-to-protect-yourself/?ocid=magicti_ta_blog)

  Key steps on how the Microsoft Incident Response team (formerly DART/CRSP) conducts ransomware incident investigations.

- [Determine the ransomware attack recovery process (May 2024)](/security/operations/incident-response-playbook-dart-ransomware-approach#step-3-determine-the-compromise-recovery-process/)

  Recommendations and best practices

- [Navigating recent ransomware threats (June 2024)](https://techcommunity.microsoft.com/t5/microsoft-security-experts-blog/octo-tempest-hybrid-identity-compromise-recovery/ba-p/4166783)
