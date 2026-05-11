---
title: Establish an Access and Identities discipline
description: Use the Microsoft security adoption model to modernize and secure identity and access across the business, based on Zero Trust principles.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to modernize and secure identity and access across the business.
---

# Establish an Access and Identities discipline

This article helps security and technology teams establish and modernize a Security Architecture discipline that provides a clear, end‑to‑end technical vision for security across the organization.

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).

This article helps security and technology teams establish and modernize an Access and Identities discipline that protects access to business assets, enables productivity, and reduces organizational risk.

## Why this discipline?

Access and identity is the security discipline that most people interact with first—and most often. Users experience it every time they sign in to a device, access an application, share a file, connect remotely, or use physical credentials to enter a building.

Because access controls sit at the intersection of security and productivity, they directly influence both organizational risk and user experience.

The Access and Identities discipline:

- 
- **Reduces risk** by shaping and governing access paths to business assets, ensuring the right entities have the right access under the right conditions, while preventing abuse by attackers.
- **Enables productivity** by consistent, low‑friction access that discourages insecure workarounds and shadow IT
- **Provides a common strategy** that security leaders and practitioners can align to and execute consistently across the organization

Access and identities is a strategic priority because identities are the most common entry point for attacks. Techniques such as password spray, phishing, token theft, pass‑the‑hash, and pass‑the‑ticket are routinely used to gain an initial foothold. Nearly all multistage attacks rely on identity compromise to move laterally, escalate privileges, and reach high‑value assets.

Without an effective Access and Identities discipline, organizations face increased risk from:

- **External compromise**: Attackers can rapidly take over legitimate user or service identities, including privileged accounts, and use them to discover and exploit business assets.
- **Insider abuse and privilege misuse**: Malicious, negligent or compromised insiders can abuse elevated privileges to access sensitive systems and data.
- **Productivity loss and insecure workarounds**: Overly restrictive or inconsistent access controls frustrate users and drive the adoption of shadow IT with weaker controls and imited visibility, increasing risk and blast radius.

## Mission and outcomes

An effective Access and Identities discipline is built around two complementary strategic objectives:

- **Secure general access** - Increase baseline security across all organizational assets by consistently enforcing minimum security assurances for everyday access.
- **Secure privileged access** - Protect access that can have material business impact, including high‑value business assets, IT administrative accounts, workload identities, and artifacts that grant broad or deep control. 

Together, these objectives ensure that access security scales with business value and risk, providing strong protection where it matters most, without unnecessarily obstructing routine work.

The following diagram illustrates these two complementary goals:

:::image type="content" source="./media/security-adoption-discipline-access-strategy.png" alt-text="Diagram of two strategic goals for access security: securing general access and securing privileged access." lightbox="./media/security-adoption-discipline-access-strategy.png":::

## Manage change

Traditional access control models focused on network perimeters, layering identity systems and VPNs around a trusted internal network. These models no longer meet the needs of modern enterprises that operate across cloud, SaaS, mobile, AI, and hybrid environments. Legacy approaches often result in:

- Fragmented solutions across identity, network, and application layers.
- Weak or inconsistent privileged access protection.
- Poor integration with security operations and detection.
- Gaps that attackers routinely exploit.


The following diagram illustrates this limitation:

:::image type="content" source="./media/security-adoption-discipline-access-fragment.png" alt-text="Diagram of legacy access control with isolated systems and gaps in privileged access security." lightbox="./media/security-adoption-discipline-access-fragment.png":::

A modern Access and Identities discipline goes beyond individual technologies. It focuses on business priorities, integration, and completeness across all access paths, while enforcing a single, coherent access strategy. Modern access control must be:

- **Secure:** Explicitly validate users, devices, and workloads using rich signals. Prevent unauthorized privilege escalation, and protect privileged access.
- **Consistent and comprehensive:** Cover all access paths—human and non‑human—and apply security assurances uniformly to eliminate gaps and improve user experience.
- **Integrated:** Use centralized policy and a minimal number of policy engines to enforce controls consistently at scale, avoiding configuration drift. 
- **Identity-centric**: Prioritize identity‑based controls, which provide richer context than network‑only signals. Use network controls as a complementary layer, not the primary trust boundary.
- 
This diagram from the [Enterprise Access Model](security-adoption-discipline-identity-access-enterprise-model.md) illustrates all of the different types of access paths an organization must secure across multiple workloads, multiple clouds, various business sensitivity levels, and access by both people and devices.

:::image type="content" source="./media/security-adoption-discipline-access-enterprise.png" alt-text="Diagram of the Enterprise Access Model showing secure, consistent, and integrated access paths across users, devices, and workloads." lightbox="./media/security-adoption-discipline-access-enterprise.png":::


## Discipline roles and collaborators

Planning and delivery of the Access and Identities discipline is typically owned by teams responsible for identity, access, and networking.
In larger organizations, responsibilities are distributed across formal roles and processes. In smaller organizations, roles may be combined and handled more informally. In all cases, documenting access and identity strategy as it evolves is strongly recommended. 

Primary roles include:

- **Access architects**: Define end‑to‑end access strategy and design across identity, networking, application, and platform layers.
- **Identity and networking engineers and operators**: Implement, operate, and maintain identity systems, access enforcement, and supporting infrastructure.

Architects must understand all access technologies holistically. Engineers typically have deep expertise in identity and/or networking systems.

Key internal collaborators include:

- **Security and enterprise architects**, to align access controls with broader security architecture and priorities
- **Engineering and operations teams**, who implement access requirements in platforms and workloads**
- **Security leaders (CISO and delegates)**, who provide direction and oversight
- **Developers**, who design and build applications using modern identity and access patterns

No single role owns access in isolation. Successful access control depends on shared responsibility and coordination across teams.

## Strategy components

An effective access and identity strategy secures the full lifecycle of authorized actions. Conceptually, this mirrors the structure of a sentence:

- **Identity subject** – who or what is requesting access.
- **Access verb** – the action being performed.
- **Access object** – the asset being accessed.

### Identity subject (who)

Access security starts with knowing who or what is requesting access:

- **All identity types**: Secure human users, workload identities, AI agents, applications, service principals, certificates, and cryptographic keys.
- - **The full identity lifecycle1**: The full identity lifecycle
Manage identities from creation, through changes and privilege elevation, to deprovisioning and return to no identity when access is no longer required.
- **Identity sources**: Define which internal and external identity providers are trusted, how identities are governed, and how lifecycle controls are enforced across those sources.

### Access verb (how)

Access enforcement must cover all assets and access paths across the entire access cycle.

- **Comprehensive coverage**: Enforce policy for cloud, on‑premises, SaaS, AI, IoT, and OT assets, across interactive access, APIs, and machine‑to‑machine communication.
- **Intermediary systems**: Secure devices, directories, gateways, VPNs, and access proxies that mediate access.
- **Consistent policy**: Apply policy uniformly across general access, privileged access, network access, external access, and workload‑level authorization models.
- **Adaptive access**: Continuously evaluate whether identities are known, trusted, and allowed using real‑time signals, and terminate sessions if risk changes.
- **Strong authentication**: Enforce phishing‑resistant authentication and mechanisms that mitigate password‑based attacks.
- **Modern access mechanisms**: Enforce least privilege at the application level and replace legacy perimeter technologies with identity‑centric approaches such as Security Service Edge (SSE).

### Access object (what)

Access policy must reflect business value, sensitivity, and governance requirements:

- **Align policy to business**: Classify assets and align access controls to their value and risk.
- **Manage control relationships**: Access strategies must account for transitive control relationships in the security graph. If A controls B and B controls C, A effectively controls C—dramatically increasing blast radius.
- **Reduce technical debt**: Retire insecure legacy protocols and cryptography (such as LM/NTLM) that undermine access assurances. This often requires coordinated action across identity, endpoints, and infrastructure.



## Alignment with other disciplines

The Access and Identities discpline does not operate independently. It aligns closely with other security disciplines, including:

- **Strategy, Integration, and Governance**.  Access decisions shape business risk and prioritization.
- **Security Architecture**: Access controls enforce architectural decisions.
- **Security Operations**: Identity telemetry and access signals feed detection, investigation, and response.
- **Endpoint Security**: Device posture directly influences access trust.
- **Data Security**: Access policies reflect data sensitivity and governance.

This alignment ensures access decisions support end‑to‑end security outcomes, not fragmented controls.


## Alignment with technology pillars

The Access and Identities discipline spans all technology pillars and serves as a unifying control layer across them, as shown in this diagram.

:::image type="content" source="./media/security-adoption-discipline-access-pillar.png" alt-text="Diagram of technology pillars showing how access and identity protections span identities, endpoints, and infrastructure." lightbox="./media/security-adoption-discipline-access-pillar.png":::


**Pillar** | *Access and Identities role**
--- | ---
**Identities** | Authentication, authorization, lifecycle management, and privilege control define who can access assets and under what conditions.
**Endpoints**| DEndpoint posture and credential protection influence access trust decisions. Compromised devices undermine identity controls.
**Infrastructure**| Identity systems and administrative interfaces run on infrastructure and require strong privileged access protection.
**Apps** | Applications must use modern identity patterns and enforce least‑privilege access for users, APIs, and pipelines.
**Data** | Identity‑based access controls govern who can read, modify, or exfiltrate sensitive data.
**Network**|  Network controls complement identity‑centric access by mitigating legacy attacks and supporting Security Service Edge (SSE) patterns.
**AI** | AI agents and services introduce new identity types that require lifecycle management, least privilege, and monitoring.


## What's next?

Microsoft Unified offers cybersecurity reference architectures, Zero Trust guidance, and expert-led workshops to help organizations with end to end security architecture.

- **Architecture and strategy workshops** - The Security Adoption Framework (SAF) - Access and Identities workshop focuses on accelerating Access and Identity modernization. This workshop is available as a less than four-hour discussion focused on key learnings and best practices.
- **Technology adoption workshops** - Microsoft Unified has workshops to help organizations learn about, plan, implement, and optimize the use of Microsoft Access and Identity technologies including Microsoft Entra and Microsoft Intune.


:::image type="content" source="./media/security-adoption-discipline-access-workshop.png" alt-text="Diagram of Microsoft Unified workshops for Access and Identity technology adoption, showing key phases and activities." lightbox="./media/security-adoption-discipline-access-workshop.png":::

## What's next?

Make sure you've [reviewed the other security disciplines](security-adoption-discipline-overview.md).