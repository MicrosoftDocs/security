---
title: Identify and protect critical business assets
description: Use the Microsoft security adoption model to secure critical assets based on Zero Trust principles and security best practices.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand I can use the Microsoft security adoption model to protect my critical organizational resources and assets.
---

# Identify and protect critical assets

This business scenario is part of our structured adoption model that helps you to achieve business goals using a modern security approach grounded in Zero Trust principles. 

Use this guidance to achieve the following business outcome: **Identifying and protecting critical business assets**.

As a business leader, you need to ensure that the most valuable assets (data, systems, and access rights) that run your business are protected against sophisticated threats. This article helps you and your security team identify and safeguard what matters most. 

## Why critical asset protection requires a new approach

Organizations rely on the availability, integrity, and confidentiality of their business systems and data to run their business operations, accept customer revenue, fulfill their mission, and more. When threat actors (cybersecurity attackers) compromise the assurances of these system and data assets, organizations face direct costs as well as risks to life, safety, mission, revenue, reputation, market share, and more. 

This diagram illustrates how these business critical assets must be secured at a level greater than others. 

:::image type="content" source="./media/security-adoption-protect-critical.png" alt-text="Diagram illustrating two categories of business critical assets: high-value assets with intrinsic business value, and privileged access accounts and systems that control those assets." lightbox="./media/security-adoption-protect-critical.png":::

Not all systems and data carry equal business impact. Business‑critical assets fall into two categories. 

- **High value assets** - High‑value assets are systems and data whose compromise could cause severe financial or operational damage, up to and including bankruptcy or insolvency, and are . These assets are often targeted for theft, extortion, or destruction.
- **Privileged access** -  Privileged access represents concentrated risk—identities, accounts, and tools that control high‑value assets. Compromise of privileged access (via IT admin accounts, workstations, and other systems) enables widespread impact and must be protected at the same level or above the level of high‑value assets.

## Business value 

The value of securing critical assets benefits the entire organization, but differs by role.

| **Roles** | **Value** |
| --- | --- |
| **Business leadership** | Protect the most valuable organizational assets that drive revenue, mission success, and competitive advantage.<br/><br/>Minimize business impact from attacks targeting high-value systems and data. <br/><br/>Ensure privileged access is secured to prevent unauthorized control of critical assets. |
| **Technology roles** | Focus security investments on the assets that matter most to the business. <br/><br/>Reduce the blast radius of breaches by securing privileged access pathways. <br/><br/>Implement standardized protections for identified critical assets across the technical estate. |
| **Security roles** | Prioritize security efforts based on business impact rather than technical complexity. <br/><br/>Establish clear visibility into critical assets and privileged access pathways. <br/><br/>Implement defense-in-depth controls for high-value targets most likely to be attacked. |

## Align security disciplines

Security disciplines represent the structured areas of accountability required to deliver this business scenario. 

- Planning and oversight disciplines define the strategy, governance, and cross‑organization coordination required.
- Technical strategy disciplines define the architectural, operational, and control capabilities required.
- Operational disciplines ensure that security controls remain effective over time through monitoring, response, and continuous improvement. They detect misuse, respond to threats, and drive ongoing security posture improvements. 

### Planning and oversight disciplines

**Discipline** | **Action**
--- | ---
**[Strategy, integration, and governance](security-adoption-discipline-strategy.md)** | Establish clear strategy, governance, policy, and processes to guide teams on identifying and prioritizing business critical assets and privileged access.<br/><br/>Drive a continuous learning approach to continuously improve your ability to identify, protect, detect, respond, recover, and govern business critical assets and privileged access. <br/><br/>Ensure governance drives and monitors cross-team processes to ensure a coordinated approach across security, technology, and business teams.
**[End-to-end security architecture](security-adoption-discipline-architecture.md)** | Ensure that security architectures explicitly require, include, and prioritize security of privileged access and high value business critical assets.<br/><br/> Ensure technical controls and capabilities are sufficient to mitigate risk across the full security lifecycle (identify, protect, detect, respond, recover, and govern). <br/><br/>Drive an integrated approach across technology teams to prioritize business critical assets and rapidly apply learnings to keep up with attacker evolution.

### Technical strategy disciplines

**Discipline** | **Action**
--- | ---
**[Access and identities](security-adoption-discipline-identity-access.md)**  | Implement privileged access management with just-in-time and just-enough-access principles. <br/><br/>Secure administrative accounts with phishing-resistant credentials and enhanced monitoring <br/><br/>Ensure critical systems require strong authentication and enforce least-privilege access. <br/><br/> Establish clear visibility into who has privileged access to critical assets.
[**Infrastructure security**](security-adoption-discipline-infrastructure.md) | Harden and closely monitor infrastructure hosting critical business applications and data. <br/><br/>Implement network segmentation to isolate high-value assets. <br/><br/>Deploy enhanced logging and anomaly detection for privileged access to critical infrastructure. <br/><br/> Establish secure baselines and configuration management for critical systems.
[**Development security**](security-adoption-discipline-development.md)| Prioritize security testing and threat modeling for applications that process or access critical business data. <br/><br/>Implement secure development practices and supply chain security for business-critical applications. <br/><br/>Establish application-level controls to protect sensitive data and prevent unauthorized access.
[**Data security**](security-adoption-discipline-data.md) | Classify and label critical business data to enable appropriate protection controls.<br/><br/>Implement data loss prevention, encryption, and access controls aligned with data criticality. <br/><br/>3. Monitor for unusual data access patterns and potential exfiltration of high-value information.
[**OT and IoT security**](security-adoption-discipline-iot.md)| Identify IoT and OT systems that are business critical or can impact physical safety. <br/><br/>Implement network segmentation and enhanced monitoring for these systems. <br/><br/>Secure privileged access to operational technology management platforms.

### Operational disciplines

**Discipline** | **Action**
--- | ---
[**SecOps**](security-adoption-discipline-security-operations.md) | Prioritize monitoring and response for critical assets and privileged access. <br/><br/>Implement enhanced threat hunting and detection for attacks targeting high-value systems. <br/><br/>Establish accelerated incident response procedures for breaches involving critical assets. <br/><br/>Use threat intelligence to anticipate attacks on valuable targets.
[**Security posture management**](security-adoption-discipline-posture.md)  | Continuously assess security posture of critical assets and privileged access pathways. <br/><br/>Prioritize vulnerability remediation based on asset criticality and business impact. <br/><br/>Monitor compliance with security baselines for high-value systems. <br/><br/>Track and report on the security status of business-critical assets to leadership.

## Required technology pillars

Technology pillars represent the core Microsoft security capabilities that support this business scenario.

**Pillar** | **Purview** | **Entra**
--- | --- | --- 
**Identity** |  Microsoft Purview integrates with  Conditional Access to enforce identity-based access controls on sensitive data through sensitivity labels and data loss prevention policies. | Microsoft Entra provides Conditional Access, and identity governance to ensure that only authorized users and services can access sensitive data.
**Endpoints** | Microsoft Purview Endpoint DLP extends data protection policies to endpoints, preventing unauthorized data transfers and ensuring sensitive information stays protected on devices. | Microsoft Entra Enforces device-based access controls, ensuring only compliant and trusted devices can access protected data.
**Networks** |  Microsoft Purview monitors data movement across network boundaries and integrates with network security tools to detect and prevent data exfiltration. | Microsoft Entra applies location and network-based access conditions through Conditional Access policies.
**Apps** | Microsoft Purview applies sensitivity labels and DLP policies across Microsoft 365 apps, SaaS applications, and on-premises file shares to ensure consistent data protection. | Microsoft Entra controls access to applications using single sign-on (SSO), application registration, and access policies.
**Data** |  Microsoft Purview provides the core data security capabilities including sensitivity labeling, data classification, data loss prevention, information barriers, and records management. | Microsoft Entra enforces access decisions using RBAC, Privileged Identity Management (PIM), and just-in-time access for sensitive operations.
**Infrastructure** | Microsoft Purview extends data governance and protection to cloud infrastructure through integration with Azure services, multicloud environments, and on-premises data stores. | Microsoft Entra governs administrative access to cloud resources through role assignments, access reviews, and privileged role protections.
**AI** | Microsoft Purview provides AI security and governance capabilities including AI Hub for visibility into AI usage, sensitivity labels for AI-generated content, and compliance controls for Copilot and other AI services. | Microsoft Entra secures access to AI services by enforcing identity verification, access policies, and governance over who can access and configure AI workloads.


## What's next?

[Learn about protecting privileged access](security-adoption-scenario-privileged-access.md).