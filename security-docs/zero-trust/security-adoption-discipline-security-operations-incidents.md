---
title: Plan for incident response in the security adoption model.
description: Understand incident response planning.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want plan our SecOps approach to incident response.
---

# Plan incident response 

This article helps with designing incident response solutions. It's intended for all roles involved in planning or design, including security operations (SecOps) leaders and architects, IT leaders, and business stakeholders.

Incident response is a core capability of the [SecOps](security-adoption-discipline-security-operations.md) discipline.

Effective incident response enables organizations to investigate, contain, and recover from active cyberattacks while minimizing business, operational, legal, and reputational impact—aligned with Zero Trust principles.



## Incident response overview 

Incident response is the practice of investigating and remediating active attack campaigns against your organization.

Incident response has the largest direct influence on critical SecOps metrics, particularly:

- **Mean Time to Acknowledge (MTTA)**. The time it takes your team to acknowledge an alert or incident after it's generated.
- **Mean Time to Remediate (MTTR)**. The time it takes to fix a security incident after it's been acknowleged.

Reducing these metrics lowers organizational risk and limits attacker impact.

Successful incident response depends on close collaboration between incident responders, threat hunting, threat intelligence, IT operations, legal, communications, and leadership teams.

## Incident response playbooks

Incident response playbooks provide scenario‑specific, step‑by‑step guidance that helps SecOps teams respond quickly and consistently to common attack techniques.

Playbooks are a critical planning output. They are developed, reviewed, and validated before incidents occur so responders can execute investigations and containment actions under pressure without having to design workflows in real time.

Microsoft publishes incident response playbooks based on best practices from Microsoft Incident Response, with guidance for common attack scenarios, including:

- Phishing
- Password spray
- App consent grant abuse
- Compromised or malicious applications

Each incident response playbook includes:

**Playbook** | **Details**
**Prerequisites** | Required logging, roles, permissions, and configuration needed before an investigation can begin.
**Workflow** | A recommended investigation flow that clarifies sequencing and dependencies.
**Checklist** | A task‑oriented checklist that supports execution, especially in regulated or audited environments.
**Investigation steps** | Detailed, step‑by‑step guidance tailored to the specific attack technique.

Playbooks complement, but do not replace, incident response plans, recovery procedures, or executive decision‑making processes. Instead, they operationalize your incident response strategy by turning detections into repeatable, high‑confidence response actions.

## Principles for effective response

Regardless of the specific tools or processes you use, effective incident response requires consistent application of the following principles.

- **Stay calm and focused**: Security incidents are disruptive and emotionally charged. Maintain focus on the highest-impact actions first.
- **Balance urgency with precision**: Act quickly to contain threats, but validate actions to avoid unintended damage, loss of evidence, or incomplete remediation.
- **Do no harm**: Ensure response actions do not:

    - Destroy forensic evidence
    - Cause unnecessary business disruption
    - Prevent root-cause analysis and learning
- **Involve legal early**: Legal guidance is critical for:
    - Law enforcement involvement
    - Regulatory and privacy notifications
    - External communications
    - Preserving privilege
- **Control information sharing**: Public or customer-facing communications should occur only with legal guidance, to avoid liability and misinformation.
- **Get help when needed**: Large or sophisticated attacks often require deep, specialized expertise, including external responders, vendors, or professional services.

Incident response is similar to treating a critical medical condition: the system is critically important, cannot be shut down, and is too complex for any single individual to fully understand.


## Balance speed and risk

During incidents, SecOps teams must consistently balance:

- **Speed vs. accuracy** – Acting fast without escalating impact
- **Transparency vs. liability** – Sharing information appropriately with investigators, leadership, and customers

It's important to follow recommended actions that reduce risk, and avoid common pitfalls, while meeting stakeholder expectations.

## Technical response best practices

Key goals during technical incident response include:

- Identify the scope of the attack
- Identify persistence mechanisms
- Determine the attacker’s objective, when possible

Persistent attackers often return if their objectives are not fully disrupted.

Recommended practices include:

- **Avoid uploading files to public scanners**:Adversaries monitor services like VirusTotal for discovery of targeted malware.
- **Carefully consider system modifications**: Only make changes when the risk of inaction outweighs the business impact. Document all incident-driven changes for rollback during recovery.
- **Ruthlessly prioritize investigation**: Focus analysis on resources the attacker actually used or modified. Full forensic coverage is often infeasible.
- **Share information deliberately**: Ensure internal teams and approved external investigators share findings under legal guidance.
- **Integrate deep system expertise**: Include platform, application, and infrastructure experts—not only security generalists.
- **Plan for reduced capacity**: Assume 50% of staff operating at 50% efficiency due to stress and fatigue.
- **Manage expectations**: In some incidents, identifying the initial access vector may be impossible due to deleted or unavailable telemetry.

## Operations response best practices

Operational coordination is equally critical.

Key goals include:

- Maintaining focus on business-critical assets
- Establishing role clarity and decision authority
- Managing business and operational impact

Recommended practices:

- **Use an Incident Command System (ICS)**: If no standing crisis organization exists, ICS provides a temporary structure.
- **Preserve daily SecOps operations**: Detection, triage, and monitoring must continue during investigations.
- **Avoid panic-driven purchases**: Do not acquire tools you cannot deploy and operate during the incident.
- **Escalate to platform owners and vendors**: Ensure access to deep expertise for operating systems, applications, and core infrastructure.
- **Define information flows early**: Set expectations for updates to executives and stakeholders.

## Technical recovery best practices

Recovery should be deliberate, consolidated, and fast.

Key goals include:

- Limit scope so recovery can occur within 24 hours when possible
- Avoid distractions not directly tied to recovery

Recommended practices:

- **Do not reset all passwords at once**: Prioritize known compromised accounts, especially administrator and service accounts. Use staged resets for users when necessary.
- **Consolidate recovery actions**: A coordinated “Big Bang” remediation limits attacker adaptation.
- **Use existing tools first**: Leverage tools already deployed and understood.
- **Avoid tipping off the attacker**: Assume attackers may have access to production data and email.

Microsoft’s Security Operations Center uses a non-production Microsoft 365 tenant for secure IR collaboration.

## Operations recovery best practices

Key goals include:

- Clear plan ownership
- Controlled scope
- Continuous stakeholder communication

Recommended practices:

- **Designate a recovery lead**: Centralized decision-making prevents confusion.
- **Understand limits**: Bring in external expertise when teams are overwhelmed or inexperienced.
- **Capture lessons learned**: Update SecOps playbooks, procedures, and role-specific guidance.

Executive and board communications are significantly more effective when planned and rehearsed in advance.

## Incident response process for SecOps

### Decide and act

When tools such as Microsoft Defender XDR or Microsoft Sentinel create an incident:

- MTTA ends when an analyst takes ownership
- MTTR begins when remediation starts

Based on confidence and scope, analysts choose between:

- Clean as you go – Early-stage incidents
- Big Bang remediation – Entrenched adversaries with persistence

Partial remediation often alerts the attacker and escalates damage.

Common remediation actions include:

- Endpoints – Isolate and reimage
- Servers and applications – Coordinate remediation with owners
- User accounts – Disable, reset credentials, expire tokens, validate MFA
- Service accounts – Coordinate with owners and IT operations
- Email – Remove malicious messages and preserve originals
- Other actions – Revoke app tokens, reconfigure services


### Post-incident cleanup

Effective incident response is incomplete without institutional learning.
Post-incident activities include:

- Recording Indicators of Compromise (IoCs)
- Addressing unknown or unpatched vulnerabilities
- Enabling or improving logging and telemetry
- Updating security baselines
- Improving response processes and playbooks

These improvements reduce manual effort and shorten response times in future incidents.

## What's next

[Review](security-operations-playbook-phishing.md) a sample phishing playbook.