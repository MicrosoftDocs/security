---
title: Adopt and secure AI and data 
description: Use the Microsoft security adoption model to rapidly adopt and secure AI based on Zero Trust principles.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: concept-article

#customer intent: As a business leader or security adopter, I want to understand I can use the Microsoft security adoption model to quickly adopt and secure AI, including data.
---

# Accelerate and secure AI adoption

This article explains how to rapidly and securely adopt AI using Zero Trust principles, as part of the Microsoft [security adoption model](security-adoption-model.md).

This business scenario helps you achieve the following outcome:

**Rapidly and securely adopt AI technology** 

As a business leader, you're under pressure to adopt AI quickly for competitive advantage, while protecting your organization from new and evolving risks. 

This business scenario is part of our [structured adoption model](security-adoption-model.md) that helps you to achieve business goals using a modern security approach grounded in Zero Trust principles. 

This guidance helps organizations adopt AI quickly and confidently while maintaining strong security, protecting sensitive data, and preserving business resilience.


## How this guidance works

This article is part of a [structured adoption model](security-adoption-model.md) that connects security strategy to implementation:

- Start with a [business scenarios](security-adoption-business-scenarios-overview.md) like this one to define the outcome you want to achieve.
- Identity the [security disciplines](security-adoption-discipline-overview.md)  that apply to this scenario. 

    Use those disciplines to define the required strategy, architecture, processes, and controls for the scenario.
    Work through each discipline to understand what needs to be planned, designed, and implemented across the organization.

- Use [technical solutions](implement-overview.md) to implement those requirements using Microsoft technologies, applying controls across [technology pillars](deploy/overview.md) such as identity and data.

This approach ensures that AI adoption is secured as part of your overall Zero Trust architecture, rather than as a separate effort.


## Why AI adoption requires a new approach

Generative AI technologies and AI agents are powerful business enablers, but they also introduce new classes of risk. These include (but aren't limited to):

- Acceleration and amplification of existing cybersecurity risk using AI.
- Unintended data exposure causing loss of intellectual property (IP) and competitive advantage.
- Alteration of data, records, or processes through attacks such as data poisoning. 

## Secure AI adoption 

To enable AI safely while managing these risks, organizations must do two things in parallel:

- **Secure AI technology** - Adopt new security controls and practices designed for AI, while reprioritizing existing security investments. For example:

    - Classify and protect sensitive data to prevent unauthorized disclosure through AI models, applications, or users.
    - Apply Zero Trust principles to AI identities, access, and data flows.
    - Extend security monitoring and controls to AI-enabled workloads and agents.

- **Use AI to improve security** — Use AI to increase the speed, scale, and effectiveness of security operations, including:
    - Security posture management.
    - Vulnerability discovery and mitigation.
    - Incident detection, investigation, and response.
    - Skills enablement for security and IT teams.

Both are required. Securing AI reduces risk, while using AI for security helps teams keep pace with the increased attack volume and sophistication driven by AI


## Business value 

The value of rapidly and securely adopting AI differs by role, but benefits the entire organization.

| **Roles** | **Value** |
| --- | --- |
| **Business leadership** | Capture new opportunities and efficiencies while limiting AI-related risks such as IP loss, reputational damage, and operational disruption. |
| **Technology roles** | Reduce incident frequency, impact, and recovery effort while lowering friction for security and compliance requirements. |
| **Security roles** | Improve the effectiveness and efficiency of security operations by using AI to detect threats faster, prioritize risks more accurately, and automate time‑consuming tasks. |

## Align security disciplines

Security disciplines represent the structured areas of accountability required to deliver this business scenario. 

- Planning and oversight disciplines define the strategy, governance, and cross‑organization coordination required.
- Technical strategy disciplines define the architectural, operational, and control capabilities required.
- Operational disciplines ensure that security controls remain effective over time through monitoring, response, and continuous improvement. They detect misuse, respond to threats, and drive ongoing security posture improvements. 


### Planning and oversight disciplines

**Discipline** | **Action**
--- | ---
**[Strategy, integration, and governance](security-adoption-discipline-strategy.md)** | Establish or update cross-team processes to ensure a coordinated approach across security, technology, and business teams, including:<br/><br/>Define a clear strategy for securing AI and using AI for security.<br/><br/>Update governance, policies, and processes to address AI‑specific risks.<br/><br/>Continuously learn and adapt as AI capabilities and threats evolve.
**[End-to-end security architecture](security-adoption-discipline-architecture.md)** | Ensure that security architecture and technical controls and capabilities include controls for AI technologies and AI usage.<br/><br/> Drive an integrated approach that allows lessons learned in one area to be rapidly applied across the organization, keeping pace with the speed of AI-driven change.


### Technical strategy disciplines

**Discipline** | **Action**
--- | ---
**[Access and identities](security-adoption-discipline-identity-access.md)** | Ensure AI agents and applications use managed, secure identities.<br/><br/>Apply least‑privilege access, informed by business priorities and threat intelligence. <br/><br/>Enable comprehensive logging and anomaly detection to support rapid response and recovery.
[**Infrastructure security**](security-adoption-discipline-infrastructure.md)| Use threat modeling to evaluate and mitigate risks introduced by AI infrastructure and AI‑enabled applications. <br/><br/>Apply AI to enhance vulnerability discovery, prioritization, and remediation. <br/><br/>Ensure robust logging and detection capabilities.
[**Development security**](security-adoption-discipline-development.md) | Evaluate application risks introduced by AI components, including both traditional software vulnerabilities and social engineering or prompt‑based manipulation.<br/><br/> Use AI to accelerate vulnerability discovery and remediation, guided by business risk and threat intelligence.<br/><br/>Support the logging of activity and detection of anomalous activity (potential attacks) to enable effective response and recovery.
[**Data security**](security-adoption-discipline-data.md)| Classify and label sensitive data to prevent AI models from ingesting or exposing it inappropriately. <br/><br/>Extend data security controls—such as data loss prevention (DLP) to cover AI applications and agents. <br/><br/>Ensure visibility and monitoring for data‑related threats.<br/><br/> Support the logging of activity and detection of anomalous activity (potential attacks) to enable effective response and recovery. 
[**OT and IoT security**](security-adoption-discipline-iot.md) | Apply threat modeling to AI interactions with OT/IoT systems, especially where AI affects physical processes. <br/><br/> Prioritize protections and monitoring based on business impact and threat intelligence.<br/><br/> Support the logging of activity and detection of anomalous activity (potential attacks) to enable effective response and recovery.

### Operational disciplines

**Discipline** | **Action**
--- | ---
[**SecOps**](security-adoption-discipline-security-operations.md) | Prepare for higher quality and higher volume of established attack techniques.<br/><br/> Integrate AI analysis to amplify and augment human activities and skills for investigating, hunting for, and simulating threats.<br/><br/>Use AI to increase skills readiness of junior analysts. Prioritize security activities using business priorities and threat intelligence insights.
[**Security posture management**](security-adoption-discipline-posture.md) | Focus on rapidly building and maturing this discipline to address increasing quality and volume of attacks accelerated by AI.<br/><br/> Integrate use of AI to more quickly analyze data, identify mitigations, and increase skills readiness of posture management professionals.

## Required technical pillars

Technology pillars represent the core Microsoft security capabilities that support this business scenario.

**Pillar** | **Purview** | **Github Advanced Security**
--- | --- | ---
**AI** | Microsoft Purview provides AI security and governance capabilities including AI Hub for visibility into AI usage, sensitivity labels for AI-generated content, and compliance controls for Copilot and other AI services. | GitHub Advanced Security applies AI-powered code analysis through Copilot Autofix to automatically suggest security fixes for identified vulnerabilities, accelerating remediation.

## Next steps

[Learn how to secure Microsoft Copilot](copilots/apply-zero-trust-copilots-overview.md).