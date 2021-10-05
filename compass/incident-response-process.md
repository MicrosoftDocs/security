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


THIS comes back to that first decision: What is our purpose: RTS or Legal? If all I care about is RTS, then I don’t care about legally admissible forensics.

Prior to an incident, KNOW what your plan is. This will help with the “Keep Calm” part below.
The Plan needs to be prioritized by the business value of the system affected. If the Café menu web site goes down is different than if BillG’s laptop goes down.

have never seen organisations respond to an incident successfully where they didn't already have a response plan and test regularly against it.  Should we say something like preparation is key to a successful IR? aka, a step before this.  Another point: detection remains the weakest of the PDR (protect,detect,respond) triad - one of the reasons we talk about integrated signal across the kill-chain and having a platform approach for rapid detection and automated response.


Although each organization’s incident response process may be different based on organizational structure and capabilities, consider this set of recommendations and best practices for responding to security incidents.

During an incident, it is critical to:

- Keep calm

   Incidents are extremely disruptive and can become emotionally charged. Stay calm and focus on prioritizing your efforts on the most impactful actions first. 

I would like us to expand on this quite a bit. Customers need to FIRST decide their objective: Return to service, or legal prosecution. The tasks will be different for each scenario.

Second, they need to prioritize the work that needs to get done. There will be only so many people working the incident. Prioritize their tasks prior to the incident

- Do no harm

   Confirm that your response is designed and executed in a way that avoids loss of data, loss of business-critical functionality, and loss of evidence. Avoid decisions can damage your ability to create forensic timelines, identify root cause, and learn critical lessons.



- Involve your legal department

   Determine whether they plan to involve law enforcement so you can plan your investigation and recovery procedures appropriately. 

- Be accurate when sharing publicly

   Confirm that anything you share with your customers and the public is based on the advice of your legal department. 

- Get help when needed

   Tap into deep expertise and experience when investigating and responding to attacks from sophisticated attackers.

Like diagnosing and treating a medical disease, cybersecurity investigation and response for a major incident requires defending a system that is both: 

- Critically important (can’t be shut down to work on it). 
- Complex (typically beyond the comprehension of any one person).

During an incident, you must strike these critical balances:

- Speed

   Balance the need to act quickly to satisfy stakeholders with the risk of rushed decisions.

- Sharing information

   Inform investigators, stakeholders, and customers based on the advice of your legal department to limit liability and avoid setting unrealistic expectations. 

This article is designed to lower risk to your organization for a cybersecurity incident by identifying common errors to avoid and providing guidance on what actions you can rapidly take that both reduce risk and meet stakeholder needs. 

## Response best practices

Responding to incidents can be done effectively from both technical and operations perspectives with these recommendations. 

>[!Note]
>For additional detailed industry guidance, see the [NIST Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf).
>

### Technical

For the technical aspects of incident response, here are some goals to consider:

- Try to identify the scope of the attack operation.

   Most adversaries use multiple persistence mechanisms.

- Identify the objective of the attack, if possible.

   Persistent attackers will frequently return for their objective (data/systems) in a future attack.

Here are some useful tips:

- Don’t make modifications

   Unless you face an imminent threat of losing business-critical data&mdash;such as deletion, encryption, and exfiltration&mdash;don’t start recovery operations until the investigation is complete. 

- Don’t investigate forever

   You must ruthlessly prioritize your investigation efforts. For example, only perform forensic analysis on endpoints that attackers have actually used or modified. In a major incident where an attacker has administrative privileges, it is practically impossible to investigate all potentially compromised resources (which may include all organization resources). 

- Share information

   Confirm that all investigation teams, including all internal teams and external investigators, are sharing their data with each other, based on the advice of your legal department. 

- Access the right expertise

   Confirm that you integrate people with deep knowledge of the systems into the investigation&mdash;such as internal staff or external entities  like vendors&mdash;not just security generalists. 

- Check with your legal department

   Determine whether they plan to involve law enforcement so you can plan your investigation and recovery procedures appropriately. 

- Anticipate reduced response capability

   Plan for 50% of your staff operating at 50% of normal capacity due to situational stress.

A key expectation to manage with stakeholders is that you may never be able to identify the initial attack because the data required for this may have been deleted before the investigation starts, such as an attacker covering their tracks by log rolling.

### Operations

For security operations aspects of incident response, here are some goals to consider:

- Staying focused

   Confirm you keep the focus on business-critical data, customer impact, and getting ready for remediation. 

- Providing coordination and role clarity

   Establish distinct roles for operations in support of the crisis team and confirm that technical, legal, and communications teams are keeping each other informed. 

- Keeping your business perspective

   You should always consider the impact on business operations by both adversary actions and your own response actions. 

Here are some useful tips:

- Consider the [Incident Command System (ICS)](https://training.fema.gov/is/courseoverview.aspx?code=is-100.c) for crisis management

   If you don’t have a permanent organization that manages security incidents, we recommend using the ICS as a temporary organizational structure to manage the crisis. 

- Keep ongoing daily operations intact

   Ensure that normal security operations are not completely sidelined to support incident investigations. This work still needs to be done.

- Avoid wasteful spending 

   Many major incidents result in the purchase of expensive security tools under pressure that are never deployed or used. If you can’t deploy and use a tool during the investigation&mdash;which can include hiring and training for additional staff with the skill sets needed to operate the tool&mdash;defer acquisition until after you finish the investigation. 

- Access deep expertise 

   Confirm you have the ability to escalate questions and issues to deep experts on critical platforms. This may require access to the operating system and application vendor for business-critical systems and enterprise-wide components such as desktops and servers. 

- Establish information flows

   Set clear guidance and expectations for the flow of information between senior incident response leaders and organization stakeholders. See [incident response planning](incident-response-planning.md) for more information. 


## Recovery best practices

Recovering from incidents can be done effectively from both technical and operations perspectives with these recommendations. 

### Technical

For the technical aspects of recovering from an incident, here are some goals to consider:

- Don’t boil the ocean

   Limit your response scope so that recovery operation can be executed within 24 hours or less. Plan a weekend to account for contingencies and corrective actions.

- Avoid distractions

   Defer long-term security investments like implementing large and complex new security systems or replacing anti-malware solutions until after the recovery operation. Anything that does not have direct and immediate impact on the current recovery operation is a distraction. 

Here are some helpful tips:

- Never reset all passwords at once

   Password resets should focus first on known compromised accounts based on your investigation and are potentially administrator or service accounts. If warranted, user passwords should be reset only in a staged and controlled manner. 

- Consolidate execution of recovery tasks

   Unless you face an imminent threat of losing business-critical data, you should plan a consolidated operation to rapidly remediate all compromised resources (such as hosts and accounts) versus remediating compromised resources as you find them. Compressing this time window will make it difficult for attack operators to adapt and maintain persistence. 

- Use existing tools

   Research and use the capabilities of tools you have already deployed before trying to deploy and learn a new tool during a recovery.

- Avoid tipping off your adversary

   As practical, you should take steps to limit the information available to adversaries about the recovery operation. Adversaries typically have access to all production data and email in a major cybersecurity incident. But in reality, most attackers don’t have time to monitor all your communications. 

  Microsoft’s Security Operations Center (SOC) has used a non-production Microsoft 365 tenant for secure communication and collaboration for members of the incident response team. 


### Operations

For the operations aspects of recovering from an incident, here are some goals to consider:

- Have a clear plan and limited scope

   Work closely with your technical teams to build a clear plan with limited scope. While plans may change based on adversary activity or new information, you should work diligently to limit scope expansion and taking on additional tasks. 

- Have clear plan ownership

   Recovery operations involve many people doing many different tasks at once, so designate a project lead for the operation for clear decision-making and definitive information to flow among the crisis team.

- Maintain stakeholder communications

   Work with communication teams to provide timely updates and active expectation management for organizational stakeholders. 

Here are some helpful tips:

- Know your capabilities and limits

  Managing major security incidents is very challenging, very complex, and new to many professionals in the industry. You should consider bringing in expertise from external organizations or professional services if your teams are overwhelmed or aren’t confident about what to do next. 

- Capture the lessons learned

  Build and continually improve role-specific handbooks for security operations, even if it’s your first incident without any written procedures.

Executive and board-level communications for incident response can be challenging if not practiced or anticipated. Make sure you have a communication plan to manage progress reporting and expectations for recovery.

## Incident response process

Consider this general guidance about the incident response process for your security operations and staff.

### 1. Decide and act

After a threat detection tool such as Azure Sentinel or Microsoft 365 Defender detects a likely attack, it creates an incident. The Mean Time to Acknowledge (MTTA) measurement of SOC responsiveness begins with the time this attack is noticed by your security staff. 

An analyst on shift is either delegated or takes ownership of the incident and performs an initial analysis. The timestamp for this is the end of the MTTA responsiveness measurement and begins the Mean Time to Remediate (MTTR) measurement.

As the analyst that owns the incident develops a high enough level of confidence that they understand the story and scope of the attack, they can quickly shift to planning and executing cleanup actions.

Depending on the nature and scope of the attack, your analysts can clean up attack artifacts as they go (such as emails, endpoints, and identities) or they may build a list of compromised resources to clean up all at once (known as a Big Bang)

- Clean as you go

   For most typical incidents that are detected early in the attack operation, analysts can quickly clean up the artifacts as they find them. This puts the adversary at a disadvantage and prevents them from moving forward with the next stage of their attack.

- Prepare for a Big Bang

   This approach is appropriate for a scenario where an adversary has already settled in and established redundant access mechanisms to your environment. This is frequently seen in customer incidents investigated by [Microsoft’s Detection and Response Team (DART)](https://www.microsoft.com/security/blog/microsoft-detection-and-response-team-dart-blog-series/). In this approach, analysts should avoid tipping off the adversary until full discovery of the attacker's presence, because surprise can help with fully disrupting their operation.

   Microsoft has learned that partial remediation often tips off an adversary, which gives them a chance to react and rapidly make the incident worse. For example, the attacker can spread the attack further, change their access methods to evade detection, cover their tracks, and inflict data and system damage and destruction for revenge.

   Cleaning up phishing and malicious emails can often be done without tipping off the attacker but cleaning up host malware and reclaiming control of accounts has a high chance of discovery.

These are not easy decisions to make and there is no substitute for experience in making these judgement calls. A collaborative work environment and culture in your SOC helps ensure that analysts can tap into each other’s experience.

The specific response steps are dependent on the nature of the attack, but the most common procedures used by analysts can include:

- Client endpoints (devices)

   Isolate the endpoint and contact the user or IT operations/helpdesk to initiate a reinstallation procedure.

- Server or applications

   Work with IT operations and application owners to arrange rapid remediation of these resources.

- User accounts

   Reclaim control by disabling the account and resetting password for compromised accounts. These procedures could evolve as your users transition to passwordless authentication using Windows Hello or another form of multi-factor authentication (MFA). A separate step is to expire all authentication tokens for the account with [Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security).

   Your analysts can also review the MFA method phone number and device enrollment to ensure it hasn’t been hijacked by contacting the user and reset this information as needed.

- Service Accounts

   Because of the high risk of service or business impact, your analysts should work with the service account owner of record, falling back on IT operations as needed, to arrange rapid remediation of these resources.

- Emails

   Delete the attack or phishing email and sometimes clear them to prevent users from recovering deleted emails. Always save a copy of original email for later search for post-attack analysis, such as headers, content, and scripts or attachments.

- Other

   You can execute custom actions based on the nature of the attack such as revoking application tokens and reconfiguring servers and services.

### 2. Post-incident cleanup

Because you don’t benefit from learned lessons until you change future actions, always integrate any useful information learned from the investigation back into your security operations. 

Determine the connections between past and future incidents by the same threat actors or methods and capture these learnings to avoid repeating manual work and analysis delays in the future. 

These learnings can take a number of forms, but common practices include analysis of:

- Indicators of Compromise (IoCs).

   Record any applicable IoCs such as file hashes, malicious IP addresses, and email attributes into your SOC threat intelligence systems.

- Unknown or unpatched vulnerabilities.

   Your analysts can initiate processes to ensure that missing security patches get applied, misconfigurations are corrected, and vendors (including Microsoft) are informed of “zero day” vulnerabilities so that they can create and distribute security patches.

- Internal actions such as enabling logging on assets covering your cloud-based and on-premises resources. 

   Review your existing security baselines and consider adding or changing security controls. For example, see the [Azure Active Directory security operations guide](/azure/active-directory/fundamentals/security-operations-introduction) for information on enabling the appropriate level of auditing in the directory before the next incident happens.

Review your response processes to identify and resolve any gaps found during the incident.

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
