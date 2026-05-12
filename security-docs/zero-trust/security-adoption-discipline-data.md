---
title: Establish a Data Security discipline during security adoption
description: Use the Microsoft security adoption model to modernize secure data across the business, based on Zero Trust principles.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to secure data cross the business.
---



# Establish a Data Security discipline

This article helps security and technology teams establish and modernize a Data Security discipline that helps organizations protect data wherever it is created, stored, processed, shared, or used, while still enabling collaboration, analytics, cloud services, and AI adoption.

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).


## Why this discipline

Data is the lifeblood of modern organizations. It underpins business operations, decision‑making, and innovation, but it is also one of the most valuable assets targeted by attackers.

Traditional, network‑centric data protection approaches are no longer sufficient in environments that use cloud services, encryption, mobile devices, and distributed collaboration. A modern Data Security discipline moves beyond perimeter controls to identity‑aware, lifecycle‑based protection, aligned to business value and risk.
Without effective data security, organizations face material business risk, including:

- Unintentional data exposure by employees using cloud service, personal devices, and AI.
- Malicious insider activity targeting sensitive information.
- Threat actors bypassing perimeter‑based controls in distributed environments.
- Ransomware and extortion attacks disrupting operations.
- Regulatory penalties, reputational damage, and—in some industries—life‑safety impacts.

A dedicated Data Security discipline provides the structure needed to reduce these risks while enabling secure and productive use of data across the organization.

## Mission and outcomes

The mission of the Data Security discipline is to protect the confidentiality, integrity, and availability of data assets throughout their lifecycle, enabling secure business operations and informed decision‑making.

A mature Data Security discipline delivers these core outcomes:

- **Data confidentiality**: Ensure only authorized users and systems can access data. 
- **Data integrity**: Prevent unauthorized alteration or corruption of data. 
- **Data availability**: Ensure data is accessible to authorized users when needed. 

Failure in these outcomes can lead to data theft and abuse, disrupt business operations, enable fraud, expose regulated data, aor even cause physical harm to people.

By establishing clear ownership, classification, and protection strategies, data security becomes an enabler of business outcomes rather than a constraint.

:::image type="content" source="./media/security-adoption-discipline-data-safety.png" alt-text="Diagram of the CIA triad illustrating confidentiality, integrity, and availability as core data security principles." lightbox="./media/security-adoption-discipline-data-safety.png":::

### Manage change

Traditional data security approaches often rely on a single control point, such as network‑based data loss prevention (DLP). This model is ineffective in modern environments because it:

- Operates only at limited points in the data lifecycle.
- Must perfectly balance protection and productivity in a single moment,
- Fails when data is encrypted, shared via cloud services, or accessed on personal devices.

This diagram summarizes the challenges to overcome using a modern approach to data security.

:::image type="content" source="./media/security-adoption-discipline-data-challenges.png" alt-text="Diagram of the data security lifecycle highlighting challenges at each stage, including creation, storage, and transfer." lightbox="./media/security-adoption-discipline-data-challenges.png":::

A modern Data Security discipline focuses on continuous visibility and control across the entire data lifecycle.

## Key focus areas

Modern data security strategies emphasize:

**Focus** | **Details**
--- | ---
**Prioritize critical data** | Protect the most business‑critical data first.
**Collaborate, coverage, visiblity** | Collaborate across the business for full visibility of structured and unstructured data across devices, apps, and clouds, preventing data silos.
**Discover data** | Know where data exists and what value or sensitivity it has.
**Classify data** | Apply consistent labels so security controls can be applied automatically.
**Lifecycle protection** | Secure data regardless of the location, technical platform, device, or environment.<br/><br/>Apply this strategy throughout the lifecycle of the data:  **create**, **consume**, **store**, **share**, and **dispose**. Secure data during creation and generation, storage at rest,  during access/sharing/use, and in transit, as well as data that is no longer active and archived or deleted. 
**Monitoring and enforcement*** | Implement real-time visibility and automated enforcement to detect and respond to real-time unauthorized access or exfiltration.
**Learn and improve** | Continuously improve data security. Adapt strategy and data controls as data formats, platforms, and use cases evolve, including AI.

This approach enables protection that scales with business and technology change.

This diagram illustrates a high level data security strategy that enables both security and productivity.

:::image type="content" source="./media/security-adoption-discipline-data-balance.png" alt-text="Diagram of a data security strategy showing Zero Trust foundation, enterprise collaboration, and data lifecycle stages." lightbox="./media/security-adoption-discipline-data-balance.png":::

In the diagram: 

- The Zero Trust foundation, shown by a dotted line, establishes a modern identity boundary and data loss prevention between internal functions and the external environment. This foundation prevents unauthorized data loss, but enables collaboration with authorized external parties.
- The enterprise collaboration environment, in lighter green, is where most of your organizational data is created, processed, and stored. Limit access to internal users only and apply least privilege by default.
- Critical apps and data, in darker green, represents the most sensitive data in the organization that must be restricted to a limited set of authorized users and applications. You can share this data within the enterprise collaboration environment and with some authorized external parties, but it must be protected and monitored at all times.

## Discipline roles and collaborators

Data security requires close collaboration across business, security, and technology teams. In larger organizations, roles are often distributed and formalized; in smaller organizations, responsibilities may be combined

Primary roles in this discipline typically include:

- Data Officer / Data Governance teams
- Data and AI architects
- Data and AI engineering and operations teams

Key collaborators include:

- **Business leaders and data owners** – Define data value, usage, and classification.
- **Security strategy and governance teams** – Define policies, standards, and oversight.
- **Architecture roles** – Integrate data security controls into system and platform designs.
- **Developers** – Implement secure data handling within applications.
- **Security‑adjacent disciplines** – Align data security with privacy, risk, and compliance efforts.

## Alignment with other disciplines

The Data Security discipline works in close coordination with other disciplines:

- **Access and Identities discipline**– Identity and access policies determine who can access data.
- **Security Architecture discipline** – Architecture defines end-to-end patterns for protecting data.
- **Security Operations (SecOps) discipline** – Detects and responds to data-related incidents.
- **Security Posture discipline** – Measures and improves data protection maturity.

Clear ownership and shared accountability are essential as data responsibilities expand.

## Alignment to technology pillars

Data travels across systems, users, and environments. As a result, the Data Security discipline spans all technology pillars.

:::image type="content" source="./media/security-adoption-discipline-data-technology.png" alt-text="Diagram of Zero Trust foundation with layers for enterprise collaboration, critical data, and technology pillars." lightbox="./media/security-adoption-discipline-data-technology.png":::



- **Identities**: Data security relies on identity security controls to enforce secure access to data through strong identity and access controls.
- **Endpoints**: Data security relies on endpoint security controls to prevent data theft from compromised or unmanaged devices.
- **Infrastructure**: Data security relies on infrastructure security controls to protect data stored or processed on servers, containers, and cloud platforms.
- **Apps**: Data security relies on app security controls to ensure apps securely access and handle sensitive data.
- **Data**: Data security relies on data security controls to discover, classify, protect, and monitor data throughout its lifecycle.
*- *Network**: Data security relies on data security controls to help discover and secure data as it is transferred between systems.
- **AI**: Data security relies on AI security controls to protect data used to train, analyze, and generate AI outputs.

## What's next?

Microsoft Unified offers expert-led workshops to help organizations accelerate modernization of Security Posture Management strategy, architecture, and technology. These workshops include:

- **Architecture and strategy workshops** - The  Security Adoption Framework Data Security workshop  workshop focuses on data security modernization. This workshop is available as a less than four-hour discussion focused on key learnings and best practices.

- **Technology adoption workshops** -  Microsoft Unified has workshops to help organizations learn about, plan, implement, and optimize the use of data techologies.

:::image type="content" source="./media/security-adoption-discipline-access-workshop.png" alt-text="Diagram of Microsoft Unified workshops for Access and Identity technology adoption, showing key phases and activities." lightbox="./media/security-adoption-discipline-access-workshop.png":::



