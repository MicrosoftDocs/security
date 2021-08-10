---
title: Incident response process | Microsoft Docs
description: Understand how to perform incident response in your security operations.
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
localization_priority: Normal
ms.topic: article
ms.prod: m365-security
---

# Incident response process

Here is a set of recommendations and best practices for responding to security incidents. Please feel free to incorporate the ones that will work within your organization's security department.

During an incident, it is critical to:

- Keep calm

   Incidents are extremely disruptive and can become emotionally charged. Stay calm and focus on prioritizing your efforts on the most impactful actions first. 

- Do no harm

   Confirm that your response is designed and executed in a way that avoids loss of data, loss of business-critical functionality, and loss of evidence. Avoid decisions can damage your ability to create forensic timelines, identify root cause, and learn critical lessons.

- Be accurate when sharing publicly

   Confirm anything you share with the public and customers is correct and truthful. 

- Get help when needed

   Investigating and responding to attacks from sophisticated attackers benefits significantly from deep expertise and experience.

Like diagnosing and treating medical disease, cybersecurity investigation and response for a major incident requires defending a system that is both: 

- Critically important (can’t be shut down to work on it) 
- Complex (typically beyond the comprehension of any one person) 

During an incident, you must strike these critical balances:

- Speed

   You must balance the need to act quickly to satisfy stakeholders with the risk of rushed decisions.

- Sharing information

   You must inform investigators, stakeholders, and customers while limiting liability and unrealistic expectations. 

This article is designed to lower risk to your business in an incident by identifying common errors to avoid and providing guidance on what actions you can take rapidly that both reduce risk and meet stakeholder needs. 

## Response best practices

Responding to incidents can be done effectively from both technical and operations perspectives with these recommendations. 

### Technology

For the technical aspects of incident response, here are some critical success factors:

- You must identify the scope of the attack operation.

   Most adversaries use multiple persistence mechanisms.

- Identify the objective of attack, if possible.

   Persistent attackers will frequently return for their objective (data/systems) in a future attack.

Here are some useful tips:

- Don’t upload files to online scanners

   Many adversaries monitor instance count on services like VirusTotal for discovery of targeted malware.

- Don’t make modifications

   Unless you face an imminent threat of losing business-critical data (deletion, encryption, exfiltration), don’t start recovery operations until the investigation is complete. 

- Don’t investigate forever

   You must ruthlessly prioritize your  investigation efforts. For example, only perform forensic analysis on endpoints that attackers have actually used or modified. In a major incident where an attacker has administrative privileges, it is practically impossible to investigate all potentially compromised resources (which may include all organization resources). 

- Share information

   Confirm that all investigation teams, including all internal teams and external investigators, are fully sharing their data with each other. 

- Access the right expertise

   Confirm you integrate people with deep knowledge of the systems into the investigation–such as internal staff or external entities  like vendors–not just security generalists. 

- Check with your legal department

   Determine whether they plan to involve law enforcement so you can plan investigation and recovery procedures appropriately. 

- Anticipate reduced response capability

   Plan for 50% of your staff operating at 50% of normal capacity due to situational stress.

A key expectation to manage with stakeholder is that you may never be able to identify the information on the initial attack because the data required for this may have been deleted before the investigation starts (such as an attacker covering their tracks and log rolling).

### Operations

For security operations aspects of incident response, here are some critical success factors:

- Staying focused

   Confirm you keep the focus on business-critical data, customer impact, and getting ready for remediation. 

- Coordination and role clarity

   Establish distinct roles for operations in support of the crisis team and confirm technical, legal and communications teams are keeping each other informed. 

- Business perspective

   You should always consider the impact on business operations by both adversary actions and your response actions. 

Here are some useful tips:

- Consider the Incident Command System (ICS) for crisis management

   If you don’t have a permanent organization that manages security incidents, we recommend using the ICS as a temporary organizational structure to manage the crisis. 

- The show must go on

   Ensure the daily security operations are not completely sidelined to support incident investigations. The normal work still needs to be done.

- Avoid wasteful spending 

   Many major incidents result in organizations purchasing an assortment of expensive security tools in a panic that are never deployed or used. If you can’t deploy and use a tool during the investigation, defer acquisition until after you finish the investigation. 

   Also consider your ability to hire, train, and retain people for any rare or specialized skill sets needed to operate or gain value from the tool. 

- Access deep expertise 

   Confirm you have the ability to escalate questions and issues to deep experts on critical platforms. This may require access to the operating system and application vendor for business-critical systems and enterprise-wide components (such as desktops and servers). 

Expectations for the flow of information between stakeholders will vary without clear guidance and input from senior incident response leaders. See [incident response planning](incident-response-planning.md) for more information.


## Recovery best practices

Recovering from incidents can be done effectively from both technical and operations perspectives with these recommendations. 

### Technology

For the technical aspects of recovering from an incident, here are some critical success factors:

- Don’t boil the ocean

   Limit your response scope so that recovery operation can be executed within 24 hours or less. Plan a weekend to account for contingencies and corrective actions.

- Avoid distractions

   Defer long-term security investments like implementing large and complex new security systems or replacing antimalware solutions until after the recovery operation. Anything that does not have direct and immediate impact on the current recovery operation is a distraction. 

Here are some helpful tips:

- Never reset all passwords at once

   Password resets should focus first on known compromised accounts based on your investigation and are potentially administrator or service accounts. If warranted, user passwords should be reset only in a staged and controlled manner. 

- Consolidate execution of recovery tasks

   Unless you face an imminent threat of losing business-critical data, you should plan a consolidated operation to rapidly remediate all compromised resources (such as hosts and accounts) versus remediating compromised resources as you find them. Compressing this time window will make it difficult for attack operators to adapt and maintain persistence. 

- Use existing tools

   Research and use the capabilities of tools you have already deployed before trying to deploy and learn a new tool during a recovery.

- Avoid tipping off your adversary

   As practical, you should take steps to limit the information available to adversaries about the recovery operation. Adversaries typically have access to all production data and email in a major cybersecurity incident. But in reality, most attackers don’t have time to monitor all your communications. Microsoft’s SOC has used a non-production Microsoft 365 tenant for secure collaboration for members of the incident response team. 

A key expectation to manage is that your first recovery attempt may not fully succeed, so you may have to try again. 

### Operations

For the operations of recovering from an incident, here are some critical success factors:

- Have a clear plan and limited scope

   Work closely with your technical teams to build a clear plan with limited scope. While plans may change based on adversary activity or new information, you should work diligently to limit “scope creep” of additional tasks. 

- Have clear plan ownership

   Recovery operations involve many people doing many different tasks at once, so designate a clear project lead for the operation for clear decision-making and good information to flow among the crisis team.

- Maintain stakeholder communications

   Work with communication teams to provide timely updates and active expectation management for organizational stakeholders. 

Here are some helpful tips:

- Know your capabilities and limits

   Managing major security incidents is very challenging, very complex, and new to many professionals in the industry. You should consider bringing in expertise from external organizations or professional services if your teams are overwhelmed or aren’t confident about what to do next. 

- Capture the lessons learned

  Build and continually improve role-specific handbooks for security operations, even if it’s your first incident without any written procedures.

Executive and board-level communications for incident response can be challenging if not practiced or anticipated. Make sure you have a communication plan to manage progress reporting and expectations for recovery.

## Incident response process

Use this general guidance about the incident response process for your security staff as needed.

### 1. Decide and act

After a threat detection tool such as Azure Sentinel or Microsoft 365 Defender detects a likely attack, it creates an incident. The Mean Time to Acknowledge (MTTA) measurement of SOC responsiveness begins with the time this attack is noticed by your security staff. 

An analyst on shift is either delegated or takes ownership of the incident and performs an initial analysis. The timestamp for this is the end of the MTTA responsiveness measurement and begins the Mean Time to Remediate (MTTR) measurement.

As the analyst that owns the incident develops a high enough level of confidence that they understand the story and scope of the attack, they can quickly shift to planning and executing cleanup actions.

Depending on the nature and scope of the attack, your analysts can clean up attack artifacts as they go (such as emails, endpoints, and identities) or they may build a list of compromised resources to clean up all at once (Big Bang)

- Clean as you go

   For most typical incidents that are detected early in the attack operation, analysts quickly clean up the artifacts as they find them. This puts the adversary at a disadvantage and prevents them from moving forward with the next stage of their attack.

- Prepare for a Big Bang

   This approach is appropriate for a scenario where an adversary has already settled in and established redundant access mechanisms to your environment. This is frequently seen in customer incidents investigated by Microsoft’s Detection and Response Team (DART). In this approach, analysts should avoid tipping off the adversary until full discovery of all attacker presence, because surprise can help with fully disrupting their operation. 

   Microsoft has learned that partial remediation often tips off an adversary, which gives them a chance to react and rapidly make the incident worse, such as spread the attack further, change access methods to evade detection, inflict damage and destruction for revenge, or cover their tracks.)
   Cleaning up phishing and malicious emails can often be done without tipping off the adversary but cleaning up host malware and reclaiming control of accounts has a high chance of discovery by the adversary.

These are not easy decisions to make and there is no substitute for experience in making these judgement calls. A collaborative work environment and culture in your SOC helps ensure that analysts can tap into each other’s experience.

The specific response steps are very dependent on the nature of the attack, but the most common procedures used by analysts can include:

- Client endpoints (devices)

   Isolate the endpoint and contact the user directly (or IT operations/helpdesk) to have them initiate a reinstallation procedure.

- Server or applications

   Work with IT operations and/or application owners to arrange rapid remediation of these resources.

- User accounts

   Reclaim control by disabling the account and resetting password for compromised accounts, although these procedures could evolve as your users transition to passwordless authentication using Windows Hello or another form of multi-factor authentication (MFA). A separate step is to expire all authentication tokens for the user with Microsoft Cloud App Security.

   Your analysts can also review the MFA method phone number and device enrollment to ensure it hasn’t been hijacked (often contacting the user) and reset this information as needed.

- Service Accounts

   Because of the high risk of service or business impact, your analysts should work with the service account owner of record and falling back on IT operations as needed, to arrange rapid remediation of these resources.

- Emails

   Delete the attack or phishing email and sometimes clear them ed to prevent users from recovering deleted emails), but always save a copy of original email for later search for post-attack analysis (such as headers, content, and scripts or attachments).

- Other
   You can execute custom actions based on the nature of the attack such as revoking application tokens and reconfiguring servers and services.

### 2. Post-incident cleanup

Because you don’t learn lessons until you change future actions, always integrate any useful information learned from the investigation back into your security operations. Capture these learnings to avoid repeating manual work in the future and see connections between past and future incidents by the same threat actors. 

These learnings can take a number of forms, but common procedures include:

- Indicators of Compromise (IoCs)

   Record any applicable IoCs such as file hashes, malicious IP addresses, and email attributes into your threat intelligence systems so that your SOC can benefit from these learnings.

- Unknown or unpatched vulnerabilities

   Your analysts can initiate processes to ensure that missing security patches get applied, misconfigurations are corrected, and vendors (including Microsoft) are informed of “zero day” vulnerabilities so that they can create and distribute security patches.

- Internal actions such as enabling logging on assets and adding or changing security controls.

## Incident response resources

- [Overview](incident-response-overview.md) for Microsoft security products and resources for new-to-role and experienced analysts
- [Planning](incident-response-planning.md) for your SOC
- [Playbooks](incident-response-playbooks.md) for detailed guidance on responding to common attack methods
- [Microsoft 365 Defender](/microsoft-365/security/defender/incidents-overview) incident response
- [Azure Sentinel](/azure/sentinel/investigate-cases) incident response

## Key Microsoft security resources 

| Resource | Description |
|:-------|:-----|
| [Microsoft Cybersecurity Reference Architectures](/security/cybersecurity-reference-architecture/mcra) | A set of visual architecture diagrams that show Microsoft’s cybersecurity capabilities and their integration with Microsoft cloud platforms such as Microsoft 365 and Microsoft Azure and third-party cloud platforms and apps. |
| [Minutes matter infographic](https://github.com/MarkSimos/MicrosoftSecurity/raw/master/Microsoft_CDOC_and_DCU_Poster.pdf) download | An overview of how Microsoft's SecOps team does incident response to mitigate ongoing attacks.  |
| [Azure Cloud Adoption Framework security operations](/azure/cloud-adoption-framework/secure/security-operations) | Strategic guidance for leaders establishing or modernizing a security operation function. |
| [Microsoft security best practices for security operations](/security/compass/security-operations) | How to best use your SecOps center to move faster than the attackers targeting your organization. |
| [Microsoft cloud security for IT architects model](https://aka.ms/cloudarchsecurity) | Security across Microsoft cloud services and platforms for identity and device access, threat protection, and information protection. |
| [Microsoft security documentation](/security/) | Additional security guidance from Microsoft. |
|||


<!--

Here are some general steps in the incident response process:


3. Examine the endpoints

   Typically, the first priority is to identify affected endpoints so your analysts can rapidly get deep insight. For example, use the Endpoint Detection and Response (EDR) functionality in Azure Sentinel or Microsoft Defender 365 for this.

4. Scope out and fill in the timeline

   The analyst then builds a full picture and timeline of the related chain of events that led to the alert (which may be an adversary’s attack operation or false alarm positive) by following leads from the first host alert. The analyst travels along the timeline:

   - Backward in time: Track backward to identify the entry point into your environment.

   - Forward in time: Follow leads to any endpoints (devices) or assets an attacker may have accessed or attempted to access.

Your analysts can build this picture using the [MITRE ATT&CK™ model](https://attack.mitre.org/) or the [Lockheed Martin Cyber Kill Chain®](https://www.lockheedmartin.com/capabilities/cyber/cyber-kill-chain.html).



When we last left our heroes in the previous entry, our analyst had built a timeline of the potential adversary attack operation. Of course, knowing what happened doesn’t actually stop the adversary or reduce organizational risk, so let’s remediate this attack!

--> 
