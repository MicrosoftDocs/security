---
title: Microsoft Incident Response ransomware approach and best practices
description: Understand how Microsoft Incident Response responds to ransomware attacks and their recommendations for containment and post-incident activities.
keywords: investigation, attack, microsoft threat protection, microsoft 365, search, query, telemetry, security events, antivirus, incident, response, incident response, playbook, guidance, Microsoft Defender XDR
search.appverid: met150
ms.service: security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords: 
- NOCSH
manager: dougeby
audience: ITPro
ms.collection: 
- msftsolution-ransomware
ms.topic: article
ms.subservice: zero-trust
ms.custom: cx-rw 
ms.date: 10/16/2024
---

# Microsoft Incident Response team ransomware approach and best practices

[Human-operated ransomware](/security/ransomware/human-operated-ransomware) isn't a malicious software problem - it's a human criminal problem. The solutions used to address commodity problems aren't enough to prevent a threat that more closely resembles a nation-state threat actor who:

- Disables or uninstalls your antivirus software before encrypting files
- Disables security services and logging to avoid detection
- Locates and corrupts or deletes backups before sending a ransom demand

These actions are often performed using legitimate programs - such as [Quick Assist](https://www.microsoft.com/security/blog/2024/05/15/threat-actors-misusing-quick-assist-in-social-engineering-attacks-leading-to-ransomware) in May 2024 - that you might already have in your environment for administrative purposes. In criminal hands, these tools are used to conduct attacks.

Responding to the increasing threat of ransomware requires a combination of modern enterprise configuration, up-to-date security products, and trained security staff to detect and respond to the threats before data is lost.

The [Microsoft Incident Response team (formerly DART/CRSP)](https://www.microsoft.com/security/blog/microsoft-detection-and-response-team-dart-blog-series/) responds to security compromises to help customers become cyber-resilient. Microsoft Incident Response provides onsite reactive incident response and remote proactive investigations. Microsoft Incident Response uses Microsoft's strategic partnerships with security organizations around the world and internal Microsoft product groups to provide the most complete and thorough investigation possible. Our incident response experts prioritize proactivity, using [daily signals and threat intelligence](https://www.youtube.com/watch?v=-JP-T4Iw1sU) to scope for threats in each customer environment. Microsoft encourages customers to also establish your own incident response team for maximum in-house perimiter monitoring.

This article describes how Microsoft Incident Response handles ransomware attacks to help guide Microsoft customers in best practices for your own security operations playbook. For information on how Microsoft uses the latest AI for ransomware mitigation, [read our article on Microsoft Security Copilot defense against ransomware attacks](https://www.microsoft.com/en-us/security/blog/2024/03/04/defend-against-human-operated-ransomware-attacks-with-microsoft-copilot-for-security).

## How Microsoft Incident Response uses Microsoft security services

Microsoft Incident Response relies heavily on data for all investigations and uses Microsoft security services such as [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security), [Microsoft Defender for Endpoint](/microsoft-365/security/office-365-security), [Microsoft Defender for Identity](/defender-for-identity), and [Microsoft Defender for Cloud Apps](/cloud-app-security/).

For the Microsoft Incident Response team's latest security measure updates, [check out their Ninja Hub](https://techcommunity.microsoft.com/blog/microsoftsecurityexperts/welcome-to-the-microsoft-incident-response-ninja-hub/4243594).

### Microsoft Defender for Endpoint

Defender for Endpoint is Microsoft's enterprise endpoint security platform designed to help enterprise network security analysts prevent, detect, investigate, and respond to advanced threats. Defender for Endpoint can detect attacks using advanced behavioral analytics and machine learning. Your analysts can use Defender for Endpoint to assess threat actor behavioral analytics.

Your analysts can also perform advanced hunting queries to identify indicators of compromise (IOCs) or search for known threat actor behavior.

Defender for Endpoint provides real-time access to expert monitoring and analysis by [Microsoft Defender Experts](/defender-endpoint/configure-microsoft-threat-experts) for ongoing suspected actor activity. You can also collaborate with experts on demand for more insights into alerts and incidents.

### Microsoft Defender for Identity

Defender for Identity investigates known compromised accounts to identify other potentially compromised accounts in your organization. Defender for Identity sends alerts for known malicious activity such as DCSync attacks, remote code execution attempts, and pass-the-hash attacks. 


### Microsoft Defender for Cloud Apps

Defender for Cloud Apps (previously known as Microsoft Cloud App Security) lets your analyst detect unusual behavior across cloud applications to identify ransomware, compromised users, or rogue applications. Defender for Cloud Apps is Microsoft's cloud access security broker (CASB) solution that allows for monitoring of cloud services and data accessed by users in cloud services.

### Microsoft Secure Score

Microsoft Defender XDR services provide live remediation recommendations to reduce the attack surface. Microsoft Secure Score is a measurement of an organization's security posture, with a higher number indicating that more improvement actions have been taken. [Read Secure Score](/microsoft-365/security/defender/microsoft-secure-score) documentation to find out more about how your organization can use this feature to prioritize remediation actions for their environment.

## The Microsoft Incident Response approach to conducting ransomware incident investigations

Determining how a threat actor gained access to your environment is crucial to identifying vulnerabilities, conducting attack mitigation, and preventing future attacks. In some cases, the threat actor takes steps to cover their tracks and destroy evidence, so it's possible that the entire chain of events might not be evident.

The following are three key steps in Microsoft Incident Response ransomware investigations:

|Step|Goal|Initial questions|
|---|---|---|
|1. Assess the current situation|Understand the scope|What initially made you aware of a ransomware attack? <BR><BR> What time/date did you first learn of the incident? <BR><BR> What logs are available and is there any indication that the actor is currently accessing systems?|
|2. Identify the affected line-of-business (LOB) apps|Get systems back online|Does the application require an identity? <BR><BR> Are backups of the application, configuration, and data available? <BR><BR> Are the content and integrity of backups regularly verified using a restore exercise?|
|3. Determine the compromise recovery (CR) process|Remove threat actor from the environment|N/A|

### Step 1: Assess the current situation

An assessment of the current situation is critical to understanding the scope of the incident and for determining the best people to assist and to plan and scope the investigation and remediation tasks. Asking the following initial questions is crucial in helping to determine the source and extent of the situation.

#### How did you identify the ransomware attack?

If your IT staff identified the initial threat such as deleted backups, antivirus alerts, endpoint detection and response (EDR) alerts, or suspicious system changes, it is often possible to take quick decisive measures to thwart the attack. These measures typically involve disabling all inbound and outbound Internet communication. While this measure might temporarily affect business operations that would typically be much less impactful than successful ransomware deployment.

If a user call to the IT helpdesk identified the threat, there might be enough advance warning to take defensive measures to prevent or minimize the effects of the attack. If an external entity such as law enforcement or a financial institution identified the threat, it's likely that the damage is already done. At this point, the threat actor might have administrative control of your network. This evidence can range from ransomware notes to locked screens to ransom demands.

#### What date/time did you first learn of the incident?

Establishing the initial activity date and time is important to help narrow the scope of the initial triage for threat actor activity. Additional questions might include:

- What updates were missing on that date? It's important to identify any exploited vulnerabilities.
- What accounts were used on that date?
- What new accounts have been created since that date?

#### What logs are available, and is there any indication that the actor is currently accessing systems?

Logs - such as antivirus, EDR, and virtual private network (VPN) - can show evidence of suspected compromise. Follow-up questions might include:

- Are logs being aggregated in a Security Information and Event Management (SIEM) solution-such as [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel/), Splunk, ArcSight, and others-and current? What is the retention period of this data?
- Are there any suspected compromised systems experiencing unusual activity?
- Are there any suspected compromised accounts that appear to be under active threat actor control?
- Is there any evidence of active command and controls (C2s) in EDR, firewall, VPN, web proxy, and other logs?

To assess the situation, you might need an Active Directory Domain Services (AD DS) domain controller that wasn't compromised, a recent backup of a domain controller, or a recent domain controller taken offline for maintenance or upgrades. Also determine whether [multifactor authentication (MFA)](https://www.microsoft.com/security/business/identity-access-management/mfa-multi-factor-authentication/) was required for everyone in the company and if [Microsoft Entra ID](https://azure.microsoft.com/services/active-directory/) was used.

### Step 2: Identify the LOB apps that are unavailable due to the incident

This step is critical in figuring out the quickest way to get systems back online while obtaining the necessary evidence.

Does the application require an identity?

- How is authentication performed?
- How are credentials such as certificates or secrets stored and managed?

Are tested backups of the application, configuration, and data available?

- Are the contents and integrity of backups regularly verified using a restore exercise? This check is important after configuration management changes or version upgrades.

### Step 3: Determine the compromise recovery process

This step might be necessary if the control plane, which is typically AD DS, has been compromised.

Your investigation should always provide output that feeds directly into the CR process. CR is the process that removes threat actor control from an environment and tactically increases security posture within a set period. CR takes place post-security breach. To learn more about CR, read the Microsoft Compromise Recovery Security Practice team's [CRSP: The emergency team fighting cyber attacks beside customers](https://www.microsoft.com/security/blog/2021/06/09/crsp-the-emergency-team-fighting-cyber-attacks-beside-customers/) blog article.

After gathering responses to the questions in steps 1 and 2, you can build a list of tasks and assign owners. Successful incident response engagement requires thorough, detailed documentation of each work item (such as the owner, status, findings, date, and time) to compile findings.

## Microsoft Incident Response recommendations and best practices

Here are Microsoft Incident Response's recommendations and best practices for containment and post-incident activities.

### Containment

Containment can only happen once you determine what needs to be contained. In the case of ransomware, the threat actor aims to obtain credentials for administrative control over a highly available server and then deploy the ransomware. In some cases, the threat actor identifies sensitive data and exfiltrates it to a location they control.

Tactical recovery is unique to your organization's environment, industry, and level of IT expertise and experience. The steps outlined below are recommended for short-term and tactical containment. [To learn more about long-term guidance, see securing privileged access](https://aka.ms/SPA). For a comprehensive view of how to defend against ransomware and extortion, [see Human-operated ransomware](/security/ransomware/human-operated-ransomware).

The following containment steps can be performed as new threat vectors are discovered.

Step 1: Assess the scope of the situation

- Which user accounts were compromised?
- Which devices are affected?
- Which applications are affected?

Step 2: Preserve existing systems

- Disable all privileged user accounts except for a small number of accounts used by your admins to help resetting the integrity of your AD DS infrastructure. If you believe a user account is compromised, disable it immediately.
- Isolate compromised systems from the network, but don't turn them off.
- Isolate at least one (and ideally two) known good domain controller in every domain. Either disconnect them from the network or turn them off to prevent the spread of ransomware to critical systems, prioritizing identity as the most vulnerable attack vector. If all your domain controllers are virtual, ensure the virtualization platform's system and data drives are backed up to offline external media that isn't connected to the network.
- Isolate critical known good application servers, such as SAP, configuration management database (CMDB), billing, and accounting systems.

These two steps can be taken concurrently as new threat vectors are discovered. To isolate the threat from the network, disable those threat vectors and then look for a known uncompromised system.

Other tactical containment actions include:

- [Reset the krbtgt password](/windows-server/identity/ad-ds/manage/ad-forest-recovery-resetting-the-krbtgt-password) twice in rapid succession. Consider using a [scripted, repeatable process](https://github.com/microsoft/New-KrbtgtKeys.ps1). This script lets you reset the krbtgt account password and related keys while minimizing the likelihood of Kerberos authentication issues. To minimize issues, the krbtgt lifetime can be reduced one or more times before the first password reset to quickly complete these steps. All domain controllers you plan to keep in your environment must be online.

- Deploy a Group Policy to the entire domain(s) that prevents privileged sign in (Domain Admins) to anything but domain controllers and privileged administrative-only workstations (if any).

- Install all missing security updates for operating systems and applications. Every missing update is a potential threat vector that ransomware actors can quickly identify and use. Microsoft Defender for Endpoint's [Threat and Vulnerability Management](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) provides an easy way to see exactly what is missing as well as the impact of missing updates.

  - For Windows 10 (or higher) devices, confirm that the current version (or n-1) is running on every device.

  - Deploy [attack surface reduction (ASR) rules](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) to prevent malware infection.

  - Enable all [Windows 10 security features](/windows/security/threat-protection/overview-of-threat-mitigations-in-windows-10).

- Check that every external facing application, including VPN access, is protected by multifactor authentication (MFA), preferably using an authentication application running on a secured device.

- For devices not using Defender for Endpoint as their primary antivirus software, conduct a full scan with [Microsoft Safety Scanner](/windows/security/threat-protection/intelligence/safety-scanner-download) on isolated known safe systems before reconnecting them to the network.

- For any legacy operating systems, upgrade to a supported operating system (OS) or decommission these devices. If these options aren't available, take every possible measure to isolate these devices, including network/VLAN isolation, Internet Protocol security (IPsec) rules, and sign-in restrictions. These steps help to ensure these systems are only accessible by the users/devices to provide business continuity.

The riskiest configurations consist of running mission critical systems on legacy operating systems as old as Windows NT 4.0 and applications, all on legacy hardware. Not only are these operating systems and applications insecure and vulnerable, but if that hardware fails, backups typically can't be restored on modern hardware. These applications can't function without legacy hardware. Strongly consider converting these applications to run on current OSs and hardware.

### Post-incident activities

Microsoft Incident Response recommends implementing the following security recommendations and best practices after each incident.

- Ensure that best practices are in place for [email and collaboration solutions](/microsoft-365/security/office-365-security/defender-for-office-365) to help prevent threat actors from using them while still letting internal users access external content easily and safely.

- Follow [Zero Trust](https://www.microsoft.com/security/business/zero-trust) security best practices for remote access solutions to internal organizational resources.

- Starting with critical impact administrators, follow best practices for account security, including using [passwordless authentication](https://www.microsoft.com/security/blog/2021/09/15/the-passwordless-future-is-here-for-your-microsoft-account/) or MFA.

- Implement a comprehensive strategy to reduce the risk of privileged access compromise.

  - For cloud and forest/domain administrative access, use Microsoft's [privileged access model (PAM)](#pam).

  - For endpoint administrative management, use the [local administrative password solution (LAPS)](#laps).

- Implement data protection to block ransomware techniques and confirm rapid and reliable recovery from an attack.

- Review your critical systems. Check for protection and backups against threat actor removal or encryption. Review and periodically test and validate these backups.

- Ensure rapid detection and remediation of common attacks against endpoint, email, and identity.

- Actively discover and continuously improve the security posture of your environment.

- Update organizational processes to manage major ransomware events and streamline outsourcing to avoid friction.

### PAM

Using the [PAM](/security/compass/privileged-access-access-model) (formerly known as the tiered administration model) enhances Microsoft Entra ID's security posture, which involves:

  - Breaking out administrative accounts in a "planed" environment, meaning one account for each level (usually four levels):

- Control Plane (formerly Tier 0): Administration of domain controllers and other crucial identity services, such as Active Directory Federation Services (ADFS) or Microsoft Entra Connect. These also include server applications that require administrative permissions to AD DS, such as Exchange Server.

- The next two planes were formerly Tier 1:

  - Management Plane: Asset management, monitoring, and security.

  - Data/Workload Plane: Applications and application servers.

- The next two planes were formerly Tier 2:

  - User Access: Access rights for users (such as accounts).

  - App Access: Access rights for applications.

- Each of these planes has a *separate administrative workstation for each plane* and only has access to systems in that plane. Accounts from other planes are denied access to workstations and servers in different planes through user rights assignments set to those devices.

The PAM ensures:

- A compromised user account only has access to its own plane.

- More sensitive user accounts can't access workstations and servers with a lower plane's security level. This helps prevent threat actor lateral movement.

### LAPS

By default, Microsoft Windows and AD DS have no centralized management of local administrative accounts on workstations and member servers. This lack of management can result in a common password for all these local accounts, or at the very least for groups of devices. This situation lets threat actors compromise one local administrator account to then access other workstations or servers in the organization.

Microsoft's [LAPS](/defender-for-identity/cas-isp-laps) mitigates this threat by using a Group Policy client-side extension that changes the local administrative password at regular intervals on workstations and servers according to the policy set. Each of these passwords is different and stored as an attribute in the AD DS computer object. This attribute can be retrieved from a simple client application, depending on the permissions assigned to that attribute.

LAPS requires the AD DS schema to be extended to allow for the additional attribute, the LAPS Group Policy templates to be installed, and installation of a small client-side extension on every workstation and member server to provide client-side functionality.

You can download LAPS from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=46899).


## Additional ransomware resources

The following Microsoft resources help detect ransomware attacks and protect organizational assets:

- [Human-operated ransomware](/security/compass/human-operated-ransomware)
- [Rapidly protect against ransomware and extortion](/security/compass/protect-against-ransomware)
- [2023 Microsoft Digital Defense Report](https://www.microsoft.com/en-us/security/security-insider/microsoft-digital-defense-report-2023) (see pages 17-26)

- [Ransomware: A pervasive and ongoing threat](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) Threat analytics report in the Microsoft Defender portal

- [Microsoft Incident Response ransomware case study](/security/ransomware/dart-ransomware-case-study)

Microsoft 365:

- [Deploy ransomware protection for your Microsoft 365 tenant](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maximize Ransomware Resiliency with Azure and Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Recover from a ransomware attack](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Malware and ransomware protection](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protect your Windows 10 PC from ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Handling ransomware in SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Threat analytics reports for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) in the Microsoft Defender portal
- [Leverage AI to defend against ransomware with Microsoft Security Copilot](/copilot/security/get-started-security-copilot)

Microsoft Defender XDR:

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

