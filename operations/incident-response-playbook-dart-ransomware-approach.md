---
title: Microsoft DART ransomware approach and best practices
description: Understand how Microsoft's Detection and Response Team (DART) responds to ransomware attacks and their recommendations for containment and post-incident activities.
keywords: investigation, attack, microsoft threat protection, microsoft 365, search, query, telemetry, security events, antivirus, incident, response, incident response, playbook, guidance, microsoft 365 defender
search.product: DART
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
  - NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
localization_priority: Normal
audience: ITPro
ms.collection: 
  - msftsolution-ransomware
ms.topic: article
ms.subservice:: m365d
ms.custom: cxdef-zt-ransomware 
---

# Microsoft DART ransomware approach and best practices

[Human-operated ransomware](/security/ransomware/human-operated-ransomware) is not a malicious software problem - it's a human criminal problem. The solutions used to address commodity problems aren't enough to prevent a threat that more closely resembles a nation-state threat actor who:

- Disables or uninstalls your antivirus software before encrypting files
- Disables security services and logging to avoid detection
- Locates and corrupts or deletes backups before sending a ransom demand

These actions are commonly done with legitimate programs that you might already have in your environment for administrative purposes. In criminal hands, these tools are used maliciously to carry out attacks.

Responding to the increasing threat of ransomware requires a combination of modern enterprise configuration, up-to-date security products, and the vigilance of trained security staff to detect and respond to the threats before data is lost.

The [Microsoft Detection and Response Team (DART)](https://www.microsoft.com/security/blog/microsoft-detection-and-response-team-dart-blog-series/) responds to security compromises to help customers become cyber-resilient. DART provides onsite reactive incident response and remote proactive investigations. DART leverages Microsoft's strategic partnerships with security organizations around the world and internal Microsoft product groups to provide the most complete and thorough investigation possible.

This article describes how DART handles ransomware attacks for Microsoft customers so that you can consider applying elements of their approach and best practices for your own security operations playbook.

See these sections for the details:

- [How DART uses Microsoft security services](#how-dart-uses-microsoft-security-services)
- [The DART approach to conducting ransomware incident investigations](#the-dart-approach-to-conducting-ransomware-incident-investigations)
- [DART recommendations and best practices](#dart-recommendations-and-best-practices)

> [!NOTE]
> This article content was derived from the [A guide to combatting human-operated ransomware: Part 1](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/) and [A guide to combatting human-operated ransomware: Part 2](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/) Microsoft Security team blog posts.

## How DART uses Microsoft security services

DART relies heavily on data for all investigations and uses existing deployments of Microsoft security services such as [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security), [Microsoft Defender for Endpoint](/microsoft-365/security/office-365-security), [Microsoft Defender for Identity](/defender-for-identity), and [Microsoft Defender for Cloud Apps](/cloud-app-security/).

### Defender for Endpoint

Defender for Endpoint is Microsoft's enterprise endpoint security platform designed to help enterprise network security analysts prevent, detect, investigate, and respond to advanced threats. Defender for Endpoint can detect attacks using advanced behavioral analytics and machine learning. Your analysts can use Defender for Endpoint for attacker behavioral analytics.

Here's an example of an alert in Microsoft Defender for Endpoint for a pass-the-ticket attack.

:::image type="content" source="./media/incident-response-playbook-dart-ransomware-approach/defender-endpoint-example-alert.png" alt-text="Example of an alert in Microsoft Defender for Endpoint for a pass-the-ticket attack" lightbox="./media/incident-response-playbook-dart-ransomware-approach/defender-endpoint-example-alert.png":::

Your analysts can also perform advanced hunting queries to pivot off indicators of compromise (IOCs) or search for known behavior if they identify a threat actor group.

Here's an example of how advanced hunting queries can be used to locate known attacker behavior.

:::image type="content" source="./media/incident-response-playbook-dart-ransomware-approach/example-advanced-hunting-query.png" alt-text="An example of an advanced hunting query." lightbox="./media/incident-response-playbook-dart-ransomware-approach/example-advanced-hunting-query.png":::

In Defender for Endpoint, you have access to a real-time expert-level monitoring and analysis service by Microsoft Threat Experts for ongoing suspected actor activity. You can also collaborate with experts on demand for additional insights into alerts and incidents.

Here's an example of how Defender for Endpoint shows detailed ransomware activity.

:::image type="content" source="./media/incident-response-playbook-dart-ransomware-approach/defender-endpoint-example-ransomware-activity.png" alt-text="Example of how Defender for Endpoint shows detailed ransomware activity." lightbox="./media/incident-response-playbook-dart-ransomware-approach/defender-endpoint-example-ransomware-activity.png":::

### Defender for Identity

You use Defender for Identity to investigate known compromised accounts and to find potentially compromised accounts in your organization. Defender for Identity sends alerts for known malicious activity that actors often use such as DCSync attacks, remote code execution attempts, and pass-the-hash attacks. Defender for Identity enables you to pinpoint suspect activity and accounts to narrow down the investigation.

Here's an example of how Defender for Identity sends alerts for known malicious activity related to ransomware attacks.

:::image type="content" source="./media/incident-response-playbook-dart-ransomware-approach/defender-for-identity-example-ransomware-alert.png" alt-text="An example of how Defender for Identity sends alerts for ransomware attacks" lightbox="./media/incident-response-playbook-dart-ransomware-approach/defender-for-identity-example-ransomware-alert.png":::

### Defender for Cloud Apps

Defender for Cloud Apps (previously known as Microsoft Cloud App Security) allows your analysts to detect unusual behavior across cloud apps to identify ransomware, compromised users, or rogue applications. Defender for Cloud Apps is Microsoft's cloud access security broker (CASB) solution that allows for monitoring of cloud services and data access in cloud services by users.

Here's an example of the Defender for Cloud Apps dashboard, which allows analysis to detect unusual behavior across cloud apps.

:::image type="content" source="./media/incident-response-playbook-dart-ransomware-approach/example-defender-for-cloud-apps-dashboard.png" alt-text="an example of the Defender for Cloud Apps dashboard." lightbox="./media/incident-response-playbook-dart-ransomware-approach/example-defender-for-cloud-apps-dashboard.png":::

### Microsoft Secure Score

The set of Microsoft 365 Defender services provides live remediation recommendations to reduce the attack surface. Microsoft Secure Score is a measurement of an organization's security posture, with a higher number indicating that more improvement actions have been taken. See the [Secure Score](/microsoft-365/security/defender/microsoft-secure-score) documentation to find out more about how your organization can leverage this feature to prioritize remediation actions that are based on their environment.

## The DART approach to conducting ransomware incident investigations

You should make every effort to determine how the adversary gained access to your assets so that vulnerabilities can be remediated. Otherwise, it is highly likely that the same type of attack will take place again in the future. In some cases, the threat actor takes steps to cover their tracks and destroy evidence, so it is possible that the entire chain of events may not be evident.

The following are three key steps in DART ransomware investigations:

|Step|Goal|Initial questions|
|---|---|---|
|1. Assess the current situation|Understand the scope|What initially made you aware of a ransomware attack? <BR><BR> What time/date did you first learn of the incident? <BR><BR> What logs are available and is there any indication that the actor is currently accessing systems?|
|2. Identify the affected line-of-business (LOB) apps|Get systems back online|Does the application require an identity? <BR><BR> Are backups of the application, configuration, and data available? <BR><BR> Are the content and integrity of backups regularly verified using a restore exercise?|
|3. Determine the compromise recovery (CR) process|Remove attacker control from the environment|N/A|

### Step 1: Assess the current situation

An assessment of the current situation is critical to understanding the scope of the incident and for determining the best people to assist and to plan and scope the investigation and remediation tasks. Asking the following initial questions is crucial in helping to determine the situation.

#### What initially made you aware of the ransomware attack?

If the initial threat was identified by IT staff-such as noticing backups being deleted, antivirus alerts, endpoint detection and response (EDR) alerts, or suspicious system changes-it is often possible to take quick decisive measures to thwart the attack, typically by disabling all inbound and outbound Internet communication. This may temporarily affect business operations, but that would typically be much less impactful than an adversary deploying ransomware.

If the threat was identified by a user call to the IT helpdesk, there may be enough advance warning to take defensive measures to prevent or minimize the effects of the attack. If the threat was identified by an external entity (like law enforcement or a financial institution), it is likely that the damage is already done, and you will see evidence in your environment that the threat actor has already gained administrative control of your network. This can range from ransomware notes, locked screens, or ransom demands.

#### What date/time did you first learn of the incident?

Establishing the initial activity date and time is important because it helps narrow the scope of the initial triage for quick wins by the attacker. Additional questions may include:

- What updates were missing on that date? This is important to understand what vulnerabilities may have been exploited by the adversary.
- What accounts were used on that date?
- What new accounts have been created since that date?

#### What logs are available, and is there any indication that the actor is currently accessing systems?

Logs - such as antivirus, EDR, and virtual private network (VPN)-are an indicator of suspected compromise. Follow-up questions may include:

- Are logs being aggregated in a Security Information and Event Management (SIEM) solution-such as [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/), Splunk, ArcSight, and others-and current? What is the retention period of this data?
- Are there any suspected compromised systems that are experiencing unusual activity?
- Are there any suspected compromised accounts that appear to be actively used by the adversary?
- Is there any evidence of active command and controls (C2s) in EDR, firewall, VPN, web proxy, and other logs?

As part of assessing the current situation, you might need an Active Directory Domain Services (AD DS) domain controller that was not compromised, a recent backup of a domain controller, or a recent domain controller taken offline for maintenance or upgrades. Also determine whether [multifactor authentication (MFA)](https://www.microsoft.com/security/business/identity-access-management/mfa-multi-factor-authentication/) was required for everyone in the company and if [Microsoft Entra ID](https://azure.microsoft.com/services/active-directory/) was used.

### Step 2: Identify the LOB apps that are unavailable due to the incident

This step is critical in figuring out the quickest way to get systems back online while obtaining the evidence required.

Does the application require an identity?

- How is authentication performed?
- How are credentials such as certificates or secrets stored and managed?

Are tested backups of the application, configuration, and data available?

- Are the contents and integrity of backups regularly verified using a restore exercise? This is particularly important after configuration management changes or version upgrades.

### Step 3: Determine the compromise recovery process

This step may be necessary if you have determined that the control plane, which is typically AD DS, has been compromised.

Your investigation should always have a goal of providing output that feeds directly into the CR process. CR is the process that removes attacker control from an environment and tactically increase security posture within a set period. CR takes place post-security breach. To learn more about CR, read the Microsoft Compromise Recovery Security Practice team's [CRSP: The emergency team fighting cyber attacks beside customers](https://www.microsoft.com/security/blog/2021/06/09/crsp-the-emergency-team-fighting-cyber-attacks-beside-customers/) blog article.

Once you have gathered the responses to the questions above, you can build a list of tasks and assign owners. A key factor in a successful incident response engagement is thorough, detailed documentation of each work item (such as the owner, status, findings, date, and time), making the compilation of findings at the end of the engagement a straightforward process.

## DART recommendations and best practices

Here are DART's recommendations and best practices for containment and post-incident activities.

### Containment

Containment can only happen once the analysis has determined what needs to be contained. In the case of ransomware, the adversary's goal is to obtain credentials that allow administrative control over a highly available server and then deploy the ransomware. In some cases, the threat actor identifies sensitive data and exfiltrates it to a location they control.

Tactical recovery will be unique for your organization's environment, industry, and level of IT expertise and experience. The steps outlined below are recommended for short-term and tactical containment steps your organization can take. To learn more about for long-term guidance, see [securing privileged access](https://aka.ms/SPA). For a comprehensive view of ransomware and extortion and how to prepare and protect your organization, see [Human-operated ransomware](/security/ransomware/human-operated-ransomware).

The following containment steps can be done concurrently as new threat vectors are discovered.

Step 1: Assess the scope of the situation

- Which user accounts were compromised?
- Which devices are affected?
- Which applications are affected?

Step 2: Preserve existing systems

- Disable all privileged user accounts except for a small number of accounts used by your admins to assist in resetting the integrity of your AD DS infrastructure. If a user account is believed to be compromised, disable it immediately.
- Isolate compromised systems from the network, but do not shut them off.
- Isolate at least one known good domain controller in every domain-two is even better. Either disconnect them from the network or shut them down entirely. The object here is to stop the spread of ransomware to critical systems-identity being among the most vulnerable. If all your domain controllers are virtual, ensure that the virtualization platform's system and data drives are backed up to offline external media that is not connected to the network, in case the virtualization platform itself is compromised.
- Isolate critical known good application servers, for example SAP, configuration management database (CMDB), billing, and accounting systems.

These two steps can be done concurrently as new threat vectors are discovered. Disable those threat vectors and then try to find a known good system to isolate from the network.

Other tactical containment actions can include:

- [Reset the krbtgt password](/windows-server/identity/ad-ds/manage/ad-forest-recovery-resetting-the-krbtgt-password), twice in rapid succession. Consider using a [scripted, repeatable process](https://github.com/microsoft/New-KrbtgtKeys.ps1). This script enables you to reset the krbtgt account password and related keys while minimizing the likelihood of Kerberos authentication issues being caused by the operation. To minimize potential issues, the krbtgt lifetime can be reduced one or more times prior to the first password reset so that the two resets are done quickly. Note that all domain controllers that you plan to keep in your environment must be online.

- Deploy a Group Policy to the entire domain(s) that prevents privileged login (Domain Admins) to anything but domain controllers and privileged administrative-only workstations (if any).

- Install all missing security updates for operating systems and applications. Every missing update is a potential threat vector that adversaries can quickly identify and exploit. Microsoft Defender for Endpoint's [Threat and Vulnerability Management](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) provides an easy way to see exactly what is missing-as well as the potential impact of the missing updates.

  - For Windows 10 (or higher) devices, confirm that the current version (or n-1) is running on every device.

  - Deploy [attack surface reduction (ASR) rules](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) to prevent malware infection.

  - Enable all [Windows 10 security features](/windows/security/threat-protection/overview-of-threat-mitigations-in-windows-10).

- Check that every external facing application, including VPN access, is protected by multifactor authentication, preferably using an authentication application that is running on a secured device.

- For devices not using Defender for Endpoint as their primary antivirus software, run a full scan with [Microsoft Safety Scanner](/windows/security/threat-protection/intelligence/safety-scanner-download) on isolated known good systems before reconnecting them to the network.

- For any legacy operating systems, upgrade to a supported OS or decommission these devices. If these options are not available, take every possible measure to isolate these devices, including network/VLAN isolation, Internet Protocol security (IPsec) rules, and login restrictions, so they are only accessible to the applications by the users/devices to provide business continuity.

The riskiest configurations consist of running mission critical systems on legacy operating systems as old as Windows NT 4.0 and applications, all on legacy hardware. Not only are these operating systems and applications insecure and vulnerable, if that hardware fails, backups typically cannot be restored on modern hardware. Unless replacement legacy hardware is available, these applications will cease to function. Strongly consider converting these applications to run on current operating systems and hardware.

### Post-incident activities

DART recommends implementing the following security recommendations and best practices after each incident.

- Ensure that best practices are in place for [email and collaboration solutions](/microsoft-365/security/office-365-security/defender-for-office-365) to make it more difficult for attackers to abuse them while allowing internal users to access external content easily and safely.

- Follow [Zero Trust](https://www.microsoft.com/security/business/zero-trust) security best practices for remote access solutions to internal organizational resources.

- Starting with critical impact administrators, follow best practices for account security including using [passwordless authentication](https://www.microsoft.com/security/blog/2021/09/15/the-passwordless-future-is-here-for-your-microsoft-account/) or MFA.

- Implement a comprehensive strategy to reduce the risk of privileged access compromise.

  - For cloud and forest/domain administrative access, use Microsoft's [privileged access model (PAM)](#pam).

  - For endpoint administrative management, use the [local administrative password solution (LAPS)](#laps).

- Implement data protection to block ransomware techniques and to confirm rapid and reliable recovery from an attack.

- Review your critical systems. Check for protection and backups against deliberate attacker erasure or encryption. It's important that you periodically test and validate these backups.

- Ensure rapid detection and remediation of common attacks on endpoint, email, and identity.

- Actively discover and continuously improve the security posture of your environment.

- Update organizational processes to manage major ransomware events and streamline outsourcing to avoid friction.

### PAM

Using the [PAM](/security/compass/privileged-access-access-model) (formerly known as the tiered administration model) enhances Microsoft Entra ID's security posture. This involves:

  - Breaking out administrative accounts in a "planed" environment-one account for each level, usually four:

- Control Plane (formerly Tier 0): Administration of domain controllers and other crucial identity services, such as Active Directory Federation Services (ADFS) or Microsoft Entra Connect. This also includes server applications that require administrative permissions to AD DS, such as Exchange Server.

- The next two planes were formerly Tier 1:

  - Management Plane: Asset management, monitoring, and security.

  - Data/Workload Plane: Applications and application servers.

- The next two planes were formerly Tier 2:

  - User Access: Access rights for users (such as accounts).

  - App Access: Access rights for applications.

- Each one of these planes will have a *separate administrative workstation for each plane* and will only have access to systems in that plane. Other accounts from other planes will be denied access to workstations and servers in the other planes through user rights assignments set to those machines.

The net result of the PAM is that:

- A compromised user account will only have access to the plane to which it belongs.

- More sensitive user accounts will not be logging into workstations and servers with a lower plane's security level, thereby reducing lateral movement.

### LAPS

By default, Microsoft Windows and AD DS have no centralized management of local administrative accounts on workstations and member servers. This usually results in a common password that is given for all these local accounts, or at the very least in groups of machines. This enables would-be attackers to compromise one local administrator account, and then use that account to gain access to other workstations or servers in the organization.

Microsoft's [LAPS](/defender-for-identity/cas-isp-laps) mitigates this by using a Group Policy client-side extension that changes the local administrative password at regular intervals on workstations and servers according to the policy set. Each of these passwords are different and stored as an attribute in the AD DS computer object. This attribute can be retrieved from a simple client application, depending on the permissions assigned to that attribute.

LAPS requires the AD DS schema to be extended to allow for the additional attribute, the LAPS Group Policy templates to be installed, and a small client-side extension to be installed on every workstation and member server to provide the client-side functionality.

You can get LAPS from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=46899).


## Additional ransomware resources

Key information from Microsoft:

- [The growing threat of ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog post on July 20, 2021
- [Human-operated ransomware](/security/compass/human-operated-ransomware)
- [Rapidly protect against ransomware and extortion](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (see pages 10-19)
- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) threat analytics report in the Microsoft 365 Defender portal
- [Microsoft DART ransomware case study](/security/ransomware/dart-ransomware-case-study)

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

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Backup and restore plan to protect against ransomware](/security/compass/backup-plan-to-protect-against-ransomware)
- [Help protect from ransomware with Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26-minute video)
- [Recovering from systemic identity compromise](/azure/security/fundamentals/recover-from-identity-compromise)
- [Advanced multistage attack detection in Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware in Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

- [Create anomaly detection policies in Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Microsoft Security team blog posts:

- [3 steps to prevent and recover from ransomware (September 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [A guide to combatting human-operated ransomware: Part 1 (September 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Key steps on how Microsoft's DART conducts ransomware incident investigations.

- [A guide to combatting human-operated ransomware: Part 2 (September 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Recommendations and best practices.

- [Becoming resilient by understanding cybersecurity risks: Part 4-navigating current threats (May 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  See the **Ransomware** section.

- [Human-operated ransomware attacks: A preventable disaster (March 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Includes attack chain analyses of actual attacks.

- [Ransomware response-to pay or not to pay? (December 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro responds to ransomware attack with transparency (December 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
