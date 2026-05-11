---
title: Enable secure remote work
description: Use the Microsoft security adoption model to enable secure remote work based on Zero Trust principles.
ms.date: 04/27/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand I can use the Microsoft security adoption model to allow people to do their job securely from anywhere
---

# Enable secure remote work

This business scenario is part of our [structured adoption model](security-adoption-model.md) that helps you to achieve business goals using a modern security approach grounded in Zero Trust principles. 

Use this guidance to achieve the following business outcome: **Enabling people to do their job securely from anywhere**.

As a business leader, you must enable your workforce to work productively from anywhere - home, office, or on the road - without compromising security. This article helps you and your security team plan enable secure remote work in a way that balances flexibility, productivity, and risk. 

## Why hybrid remote work requires a new approach

Remote work is a powerful business enabler, but it also introduces new and expanded security risks. To manage these risks while unlocking business value, organizations must take a modern, identity‑centric approach to security that protects users, devices, applications, and data wherever access occurs. To succeed organizations must:

- **Modernize traditional security:** Traditional perimeter-based security blocks productivity and is ineffective for remote and hybrid work environments. Organizations must ensure that users, devices, applications, and data are protected regardless of where or how they're accessed.
- **Secure user access:** Use multifactor authentication (MFA), Conditional Access policies, and device compliance checks to ensure only authorized users and healthy devices can access corporate resources.
- **Empower the workforce:** Provide employees with the flexibility to work productively from home, office, or on the go without compromising security, improving satisfaction and retention.
 
This scenario is foundational for modern organizations seeking to support distributed work while maintaining strong security and operational resilience.

## Business value 

The value of secure remote work varies by role, but benefits the entire organization.

| **Roles** | **Value** |
| --- | --- |
|**Business leadership**| Secure remote work enables business continuity and resilience by allowing employees to work productively from any location without increasing security or compliance risk. By shifting from perimeter-based security to an identity- and data-centric Zero Trust model, organizations reduce the likelihood of data breaches and regulatory violations while maintaining agility during disruptions. This approach supports workforce flexibility, protects organizational reputation, and enables expansion without geographic constraints.|
|**Technology roles**| Secure remote work provides a scalable, centralized framework to manage and protect a distributed environment. Identity, device, and application–based controls improve visibility across users and endpoints, while automated policy enforcement reduces operational overhead. Centralized management and automation simplify access control, accelerate incident response and recovery, and enable IT teams to support remote work reliably without increasing complexity or operational risk.|
|**Security roles**| Secure remote work allows security teams to modernize architecture and operations using Zero Trust principles, enabling business agility while improving visibility into risk and threats. Comprehensive identity, device, and application telemetry delivers actionable insights beyond traditional network data. Asset- and data-centric controls protect sensitive information across all locations, reducing the likelihood of breaches and regulatory violations through strong identity verification, device health validation, and contextual access enforcement.|

## Align security disciplines

Security disciplines represent the structured areas of accountability required to deliver this business scenario. 

- Planning and oversight disciplines define the strategy, governance, and cross‑organization coordination required.
- Technical strategy disciplines define the architectural, operational, and control capabilities required.
- Operational disciplines ensure that security controls remain effective over time through monitoring, response, and continuous improvement. They detect misuse, respond to threats, and drive ongoing security posture improvements. 

### Planning and oversight disciplines

**Discipline** | **Action**
--- | ---
**[Strategy, Integration, and Governance](security-adoption-discipline-strategy.md)** | Define clear business and security objectives for secure remote work, aligned with organizational priorities and risk tolerance.<br/><br/>Ensure cross-functional alignment across IT, security, HR, and business units.<br/><br/>Jointly define measurable goals, success criteria, and cross-team processes to guide implementation and maturity.<br/><br/>Establish governance structures to oversee policy enforcement, compliance, and decision-making throughout the remote work lifecycle.
**[Security Architecture](security-adoption-discipline-architecture.md)** | Ensure the organization has an end-to-end architecture that enables and secures remote work (access and identities).<br/><br/>Ensure response and recovery capabilities are updated (Security Operations).<br/><br/>Ensure data is appropriately protected (Data Security), and more.<br/><br/>Ensure all components are interoperable, scalable, and adaptable to evolving threats and business needs.

### Technical strategy disciplines

**Discipline** | **Action**
--- | ---
**[Access and Identities](security-adoption-discipline-identity-access.md)**| Implement strong authentication (MFA), centralized identity management, and Conditional Access policies to verify users and devices before granting access.<br/><br/> Ensure least privilege and just-in-time access for sensitive roles.<br/><br/>Secure access to applications through modern authentication, session controls, and runtime protections. <br/><br/>Ensure apps are onboarded to identity platforms and monitored for anomalous behavior.
**[Data Security](security-adoption-discipline-data.md)** | Classify and protect sensitive data using encryption, labeling, and data loss prevention.<br/><br/>Ensure data remains secure across devices, locations, and applications, with persistent access controls.
**[Infrastructure security](security-adoption-discipline-infrastructure.md)** | Secure cloud and on-premises infrastructure with segmentation, encryption, and continuous monitoring.<br/><br/>Apply Zero Trust controls to all network paths and administrative interfaces.
**[Development security](security-adoption-discipline-development.md)**| Ensure that development standards require the use of modern authentication protocols to remove the need for retrofitting security onto older protocols and mechanisms.
**[OT and IoT security](security-adoption-discipline-iot.md)** | Carefully consider business needs for remotely accessing these systems versus potential security risk of current remote access solutions and potential improvements to them.
**Application security** | Secure access to applications through modern authentication, session controls, and runtime protections.<br/><br/>Ensure apps are onboarded to identity platforms and monitored for anomalous behavior.

### Operational disciplines

**Discipline** | **Action**
--- | ---
[**SecOps**](security-adoption-discipline-security-operations.md)  | Continuously monitor remote devices, identities, and applications without traditional firewall and network intrusion detection or prevention system (IDS/IPS) telemetry.<br/><br/>Update automation, incident response playbooks, and threat hunting processes to use extended detection and response (XDR) capabilities.
[**Security posture management**](security-adoption-discipline-posture.md)| Monitor software vulnerabilities, security configurations, and operational practices across the environment.<br/><br/>Use tools like Microsoft Security Exposure Management and Secure Score to track progress and compliance, remediate gaps, and ensure alignment with Zero Trust principles.

## Required technology pillars

Technology pillars represent the core Microsoft security capabilities that support this business scenario.


**Technlogy pillar** | **Microsoft Entra** | **Microsoft Intune**
--- | --- | ---
**Cross-pillar** | Enforces access decisions using identity, authentication, and risk signals across all technology pillars. | Provides device compliance and security signals that are used to enforce access decisions across all technology pillars.
**Identity** | Manages identities, authentication, and identity protection, including risk detection and Conditional Access policy evaluation. |  Integrates with Microsoft Entra to ensure only authenticated users can enroll and manage devices.
**Endpoints** |  Evaluates device state through Conditional Access and enforces access policies based on device trust and risk. | Configures, secures, and monitors devices across platforms, enforcing compliance and security baselines.
**Networks** |  Microsoft Entra Internet Access and Microsoft Entra Private Access are Security Service Edge (SSE) technologies that converge network, identity, and endpoint access controls so you can secure access to any app or resource, from anywhere. |  Enables network access control through compliance policies and integrates with Microsoft Entra for network-aware Conditional Access decisions. Microsoft Tunnel for Mobile ensures secure, least‑privilege access to internal apps from anywhere.
**Apps** | Microsoft Entra Conditional Access protects applications by enforcing access controls and app protection policies. Conditional Access App Control integrates with Microsoft Defender for Cloud Apps to monitor and control user sessions in real time. | Enforces mobile application management (MAM) and app protection policies to secure application usage on devices.
**Data** |  Microsoft Entra Conditional Access works with sensitivity labels to enforce access requirements based on data classification, helping ensure that only authorized users on compliant devices can access sensitive content. |  Applies data protection policies such as encryption, data loss prevention, and selective wipe on managed devices.
**Infrastructure** | Microsoft Entra Workload ID helps secure the applications, service principals, and managed identities used to access your apps and infrastructure. | Extends management and security policies to cloud PCs, virtual desktops, and hybrid endpoints.
**AI** | Microsoft Entra Agent ID extends the comprehensive security capabilities of Microsoft Entra to agents, enabling organizations to build, discover, govern, and protect agent identities. | Microsoft Intune applies AI-driven insights through endpoint analytics to proactively identify device health issues, optimize user experience, and recommend security improvements.

## What's next?

[Learn how to implement secure remote work](deploy/identity.md) to design a privileged access architecture.
