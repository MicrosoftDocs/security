---
title: Microsoft DART ransomware case study
description: Understand how Microsoft's Detection and Response Team (DART) detected and responded to a ransomware attack.
keywords: investigation, attack, microsoft threat protection, microsoft 365, search, query, telemetry, security events, antivirus, incident, response, incident response, playbook, guidance, microsoft 365 defender
search.product: DART
search.appverid: met150
ms.service: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
  - NOCSH
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: 
  - M365-security-compliance
  - m365initiative-m365-defender
ms.topic: article
ms.subservice:: m365d
---

# Microsoft DART ransomware case study

Human-operated ransomware continues to maintain its position as one of the most impactful cyberattack trends world-wide and is a significant threat that many organizations have faced in recent years. These attacks take advantage of network misconfigurations and thrive on an organization’s weak interior security. Although these attacks pose a clear and present danger to organizations and their IT infrastructure and data, they are a [preventable disaster](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/).

The [Microsoft Detection and Response Team (DART)](https://www.microsoft.com/security/blog/microsoft-detection-and-response-team-dart-blog-series/) responds to security compromises to help customers become cyber-resilient. DART provides onsite reactive incident response and remote proactive investigations. DART leverages Microsoft’s strategic partnerships with security organizations around the world and internal Microsoft product groups to provide the most complete and thorough investigation possible.

This article describes how DART investigated a recent ransomware incident with details on the attack tactics and detection mechanisms.

See [Part 1](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/) and [Part 2](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/) of DART’s guide to combatting human-operated ransomware for more information.

## The attack

DART leverages [incident response tools and tactics](incident-response-process.md) to identify threat actor behaviors for human operated ransomware. Public information regarding ransomware events focuses on the end impact, but rarely highlights the details of the operation and how threat actors were able to escalate their access undetected to discover, monetize, and extort.

Here are some common techniques that attackers use for ransomware attacks based on [MITRE ATT&CK tactics](https://attack.mitre.org/).
 
:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-attack-methods.png" alt-text="Common techniques that attackers use for ransomware attacks." lightbox="media/dart-ransomware-case-study/dart-ransomware-case-study-attack-methods.png":::

DART used Microsoft Defender for Endpoint to track the attacker through the environment, create a story depicting the incident, and then eradicate the threat and remediate. Once deployed, Defender for Endpoint began detecting successful logons from a brute force attack. Upon discovering this, DART reviewed the security data and found several vulnerable Internet-facing devices using the Remote Desktop Protocol (RDP). 

After initial access was gained, the threat actor used the Mimikatz credential harvesting tool to dump password hashes, scanned for credentials stored in plaintext, created backdoors with Sticky Key manipulation, and moved laterally throughout the network using remote desktop sessions.

For this case study, here is the highlighted path that the attacker took.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-attack-path.png" alt-text="The path the ransomware attacker took for this case study." lightbox="media/dart-ransomware-case-study/dart-ransomware-case-study-attack-path.png":::

The following sections describe additional details based on the MITRE ATT&CK tactics and include examples of how the threat actor activities were detected with the Microsoft 365 Defender portal.

## Initial access

Ransomware campaigns use well-known vulnerabilities for their initial entry, typically using phishing emails or weaknesses in perimeter defense such as devices with the enabled Remote Desktop service exposed on the Internet.

For this incident, DART was able to locate a device that had TCP port 3389 for RDP exposed to the Internet. This allowed threat actors to perform a brute-force authentication attack and gain the initial foothold.

Defender for Endpoint used threat intelligence to determine that there were numerous sign-ins from known brute-force sources and displayed them in the Microsoft 365 Defender portal. Here’s an example.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-brute-force-sign-in.png" alt-text="An example of known brute-force sign-ins in the Microsoft 365 Defender portal.":::

## Reconnaissance

Once the initial access was successful, environment enumeration and device discovery began. These activities allowed the threat actors to identify information about the organization’s internal network and target critical systems such as domain controllers, backup servers, databases, and cloud resources. After the enumeration and device discovery, the threat actors performed similar activities to identify vulnerable user accounts, groups, permissions, and software.

The threat actor leveraged Advanced IP Scanner, an IP address scanning tool, to enumerate the IP addresses used in the environment and perform subsequent port scanning. By scanning for open ports, the threat actor discovered devices that were accessible from the initially compromised device. 

This activity was detected in Defender for Endpoint and used as an indicator of compromise (IoC) for further investigation. Here’s an example.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-port-scan.png" alt-text="An example of port scanning in the Microsoft 365 Defender portal.":::

## Credential theft

After gaining initial access, the threat actors performed credential harvesting using the Mimikatz password retrieval tool and by searching for files containing “password” on initially compromised systems. These actions enabled the threat actors to access additional systems with legitimate credentials. In many situations, threat actors use these accounts to create additional accounts to maintain persistence after the initial compromised accounts are identified and remediated.  

Here’s an example of the detected use of the Mimikatz in the Microsoft 365 Defender portal.
 
:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-mimikatz.png" alt-text="An example of Mimikatz detection in the Microsoft 365 Defender portal":::

## Lateral movement

Movement across endpoints can vary between different organizations, but threat actors commonly use different varieties of remote management software that already exists on the device. By utilizing methods of remote access that the IT department commonly uses in their day-to-day activities, threat actors can fly under the radar for extended periods of time. 

Using Microsoft Defender for Identity, DART was able to map out the path that the threat actor took between devices, displaying the accounts that were used and accessed. Here’s an example.
 
:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-threat-actor-path.png" alt-text="The path that the threat actor took between devices in Microsoft Defender for Identity.":::

## Defense evasion

To avoid detection, the threat actors used defense evasion techniques to avoid identification and achieve their objectives throughout the attack cycle. These techniques include disabling or tampering with anti-virus products, uninstalling or disabling security products or features, modifying firewall rules, and using obfuscation techniques to hide the artifacts of an intrusion from security products and services. 

The threat actor for this incident used PowerShell to disable real-time protection for Microsoft Defender on Windows 11 and Windows 10 devices and local networking tools to open TCP port 3389 and allow RDP connections. These changes decreased the chances of detection in an environment because they modified system services that detect and alert on malicious activity. 

Defender for Endpoint, however, cannot be disabled from the local device and was able to detect this activity. Here’s an example.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-mde-detect-powershell.png" alt-text="An example of detecting the use of PowerShell to disable real-time protection for Microsoft Defender.":::

## Persistence

Persistence techniques include actions by threat actors to maintain consistent access to systems after efforts are made by security staff to regain control of compromised systems.  

The threat actors for this incident used the Sticky Keys hack because it allows for remote execution of a binary inside the Windows operating system without authentication. They then used this capability to execute a Command Prompt and perform further attacks. 

Here’s an example of the detection of the Sticky Keys hack in the Microsoft 365 Defender portal.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-detect-sticky-keys.png" alt-text="An example of detecting the Sticky Keys hack in the Microsoft 365 Defender portal.":::

## Impact

Threat actors typically encrypt files using applications or features that already exist within the environment. The use of PsExec, Group Policy, and Microsoft Endpoint Configuration Management are methods of deployment that allow an actor to quickly reach endpoints and systems without disrupting normal operations.  

The threat actor for this incident leveraged PsExec to remotely launch an interactive PowerShell Script from various remote shares. This attack method randomizes distribution points and makes remediation more difficult during the final phase of the ransomware attack. 

### Ransomware execution

Ransomware execution is one of the primary methods that a threat actor uses to monetize their attack. Regardless of the execution methodology, distinct ransomware frameworks tend to have a common behavioral pattern once deployed:

- Obfuscate threat actor actions
- Establish persistence
- Disable windows error recovery and automatic repair
- Stop a list of services
- Terminate a list of processes
- Delete shadow copies and backups
- Encrypt files, potentially specifying custom exclusions
- Create a ransomware note 

Here’s an example of a ransomware note.

:::image type="content" source="media/dart-ransomware-case-study/dart-ransomware-case-study-ransom-note-example.png" alt-text="An example of a ransomware note.":::


## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](human-operated-ransomware.md)
- [Rapidly protect against ransomware and extortion](protect-against-ransomware.md)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (see pages 10-19)
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft 365 Defender portal
- [Microsoft DART ransomware approach and best practices](incident-response-playbook-dart-ransomware-approach.md)

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Threat analytics reports for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) in the Microsoft 365 Defender portal

Microsoft 365 Defender:

- [Find ransomware with advanced hunting](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Defender for Cloud Apps:

-  [Create anomaly detection policies in Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](backup-plan-to-protect-against-ransomware.md)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Security team blog posts:

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
