---
title: Align security adoption with industry Zero Trust frameworks
description: Learn how to Microsoft's security adoption model aligns with industry-driven Zero Trust frameworks.
ms.date: 04/27/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a Microsoft security platform adopter, I want to understand how Microsoft's security adoption model aligns with external Zero Trust frameworks.
---
# Align adoption with Zero Trust frameworks 

This article explains how Microsoft's Zero Trust adoption guidance aligns with commonly used security frameworks. It helps you understand how these frameworks relate to Zero Trust principles and how to use them to guide your security strategy.

Zero Trust isn't a single framework. It's a security model that aligns with multiple industry and government standards. These different standards aren't competing solutions. Instead, each addresses a different aspect of Zero Trust, such as defining core concepts, assessing progress, or coordinating adoption across an organization.

While these industry frameworks help define what Zero Trust should achieve, organizations still need a way to translate that guidance into security solution planning, design, and deployment. 

Microsoft's Zero Trust adoption and implementation guidance does just that. It aligns to and builds on industry frameworks to provide a structured adoption model for applying consistent security principles, architectures, and processes, helping you to adopt and implement Zero Trust security in organized, phased, and practical way.

> [!TIP]
> Microsoft offers a rich set of security adoption workshops - the *Security Adoption Framework (SAF) workshops* that align to guidance for our structured adoption model. These expert-led workshops help you plan and align your security strategy with Microsoft best practices, and with external Zero Trust frameworks such as those described in this article. Learn more about our [SAF workshops](workshop-business-overview.md).

## NIST Zero Trust

[NIST Special Publication (SP) 800‑207 Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final) establishes an industry-recognized definition of Zero Trust architecture. It explains what Zero Trust is and how trust decisions are made, independent of any specific vendor, product, or deployment roadmap.

- NIST SP 800-207 is most useful when organizations need a common, authoritative definition of Zero Trust concepts that can be shared across security, IT, and architecture teams.
- NIST explicitly positions Zero Trust as an architecture where access to resources is never implicitly trusted. 
- Zero Trust principles include assuming compromise (assuming breach) to drive a holistic and practical security approach, verifying trust explicitly before granting access to assets, and limiting the blast radius by granting the least privilege necessary.

Key architectural concepts focus on continuous dynamic evaluation of access requests using contextual signals. Centralized policy decision logic that evaluates signals against organizational policy, and policy enforcement functionality close to protected resources applies the decision.

NIST SP 800-270 doesn't define technology pillars or security domains such as identity, endpoints, or data protection. Its logical Zero Trust architecture focuses on how access decisions are evaluated and enforced using policy engines, enforcements points, and contextual signals. Identity, devices posture, apps, and data appear in the model as subjects, resources, and source of context. 

Microsoft's [security adoption model](security-adoption-model.md) builds on this architecture by focusing on Zero Trust operations. Zero Trust adoption across security disciplines and technology pillars supports business planning, ownership, design, implementation, and progress tracking.

### Implementation

Implementation guidance is provided by [NIST SP 1800-35 Implementing a Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/1800/35/final).

For implementation guidance, NIST collaborated with 24 vendors, including Microsoft, on developing a guide with practical steps for organizations eager to implement cybersecurity reference designs for Zero Trust.

Microsoft participated as one of the vendors providing technology to implement Zero Trust capabilities across identity and access management, endpoint management and configuration, threat protection and monitoring, and secure access to distributed resources.

This diagram is the result of the NIST SP 1800-35 collaboration and can be downloaded from [Microsoft Cybersecurity Reference Architecture (MCRA)](https://aka.ms/MCRA). 

:::image type="content" source="./media/adoption-map-nist.png" alt-text="Diagram showing Microsoft products mapped to NIST Zero Trust Architecture." lightbox="./media/adoption-map-nist.png":::


## CISA Zero Trust Maturity Model

The [Cybersecurity and Infrastructure Security Agency (CISA) Zero Trust Maturity Model](https://www.cisa.gov/zero-trust-maturity-model) is organized around adoption and assessment. It provides a roadmap rather than a reference architecture. It helps organizations to organize and assess current posture, prioritize improvements and track progress. 

- The model uses domain-style pillars that include Identity, Devices, Networks/Environment, Apps/Workloads, and Data.
- It looks at three cross-cutting capabilities - Visibility and Analytics, Automation and Orchestration, Governance.
- It captures four possible maturity states: Traditional, Initial, Advanced, and Optimal. 

The model maps to our recommended adoption model.

**CISA** | **Adoption discipline** | **Alignment**
--- | --- | --
**Identity - Apps & Workloads**<br/><br/>Identity covers authentication, authorization, identity risk, lifecycle; Apps & Workloads covers application access controls, workload identity, and secure application interaction. | Identity and access security. | Access in Microsoft spans both identity and application layers. CISA intentionally separates these to allow independent maturity tracking while supporting identity‑centric access decisions.
**Data**<br/><br/>Data classification, inventory, access control, encryption, and protection independent of network location. | Data security | Both models place data as a primary protection target, reinforcing the Zero Trust shift from perimeter security to data‑centric controls.
**Visibility & Analytics + Automation & Orchestration**<br/><br/>Telemetry collection, continuous monitoring, detection, response automation, and policy enforcement at scale. | SecOps | CISA’s cross‑cutting capabilities map directly to SecOps outcomes: detect threats, automate response, and continuously reassess trust across all domains.
**Apps & Workloads**<br/><br/>Application security controls, workload protection, runtime security, and secure service interactions. | Dev security | CISA’s workload focus aligns with DevSecOps goals by embedding security into application and service lifecycles rather than treating it as a post‑deployment activity.
**Devices, Networks/Environments**<br/><br/>Device inventory, posture, compliance; network segmentation, secure connectivity, environmental controls.br/><br/>Non‑traditional, constrained, and specialized devices; segmented environments and limited trust assumptions. | Infrastructure security, including OT/IoT security | Infrastructure trust is established through device health and controlled connectivity, aligning with Zero Trust’s goal of minimizing blast radius and lateral movement.<br/><br/>CISA intentionally includes OT/IoT within device and network pillars, while Microsoft elevates them as a discipline for ownership and risk management reasons.
**Maturity stages across all pillars** | Security posture | Posture management is the core purpose of the CISA model: assess current state, identify gaps, prioritize improvements, and track Zero Trust progress over time.

> [!NOTE]
> Governance isn't a specific pillar in CISA. Both CISA and Microsoft treat governance as foundational to Zero Trust adoption, ensuring business alignment, clear ownership, and measurable outcomes rather than isolated technical controls.
> Security architecture isn't a specific pillar in CISA. CISA doesn't define reference architectures. It assumes architectures exist, and evaluates capabilities regardless of design pattern.
> Microsoft fills the gaps between a conceptual architecture such as NIST SP 900-207 and adoption with the Architecture discipline. CISA on the other hand informs architectural priorities through maturity targets.

For information, see [Implementing the CISA Zero Trust Maturity Model with Microsoft cloud services](cisa-zero-trust-maturity-model-intro.md).

## The Open Group Zero Trust Reference Model

The Open Group [Zero Trust Reference Model](https://www.opengroup.org/forum/zero-trust-model) approaches Zero Trust from an enterprise capability and integration perspective. Rather than defining specific implementation steps, it describes the capabilities and governance structures that organizations need to define, integrate, and operate Zero Trust at scale. 

- **Capabilities + Architecture Building Blocks (ABBs)** define security capabilities that drive durable security outcomes and the people, process, and technology to enable them.
- **Collaboration and Integration Models** show how to integrate security with strategy, risk management, operations, and other aspects of the organization.

The capabilities are composed of people, process, and technology elements working together:

- **People**: defined as roles in [The Open Group Roles and Glossary standard](https://www.opengroup.org/togaf-roles-and-responsibilities)
- **Process**: defined as architecture building blocks (ABBs) in the same Zero Trust Reference Model standard
- **Technology**: defined as ABBs in the same Zero Trust Reference Model standard

This diagram shows these capabilities:

:::image type="content" source="./media/adoption-zero-trust-open.png" alt-text="Diagram showing The Open Group Security Capabilities from the Zero Trust Reference model." lightbox="./media/adoption-zero-trust-open.png":::

This diagram shows how these capabilities align to the functions of the NIST Cybersecurity Framework (NIST CSF):
 
:::image type="content" source="./media/adoption-zero-trust-open-capabilities.png" alt-text="Diagram that shows The Open Group Security Capabilities mapped to the NIST Cybersecurity Framework functions." lightbox="./media/adoption-zero-trust-open-capabilities.png":::

The model maps to our recommended adoption model.

**Open Group** | **Adoption discipline** | **Alignment**
--- | --- | --
**Zero Trust Strategy & Governance**<br/><br/>Defines how organizations establish Zero Trust as a business‑aligned strategy, including governance, risk management, policy ownership, and alignment of people, process, and technology. | Strategy, Integration, and Governance | Open Group explicitly positions Zero Trust as an enterprise strategy, not a technical control set. This directly supports executive alignment, ownership, and integration across the organization.
**Capability-based Zero Trust architecture**<br/><br/>Provides architectural building blocks and capability groupings to design Zero Trust architectures, without prescribing specific technologies or products. | Security architecture | This fills the space between NIST’s abstract architecture and implementation guidance, enabling architects to translate Zero Trust principles into enterprise‑scale designs.
**Identity, Authentication, Authorization, and Policy Enforcement capabilities**<br/><br/>Defines capabilities required to verify identity, evaluate trust dynamically, and enforce access decisions consistently across environments. | Identity and access | Aligns directly to access security as an adoption discipline: who can access what, under which conditions, and how that decision is enforced.
**Data‑centric protection capabilities**<br/><br/>Emphasizes protection of information regardless of location, including data classification, protection, and policy‑driven access. | Data security | Mirrors Zero Trust’s shift from perimeter security to data‑centric security, aligning naturally with data protection as an adoption domain.
**Visibility, monitoring, analytics, and response capabilities**<br/><br/>Includes capabilities for collecting telemetry, monitoring trust signals, and adapting policy based on observed risk. | SecOps | Enables continuous evaluation and enforcement — core to Zero Trust operations and security monitoring at scale.
**Application and service interaction security capabilities**<br/><br/>Addresses how applications and services participate in Zero Trust, including secure interactions, service identity, and runtime enforcement. | Dev security | Supports integrating Zero Trust into modern application lifecycles and service‑to‑service communication.
**Platform and environment security capabilities**<br/><br/>Covers secure operation of platforms, networks, and environments that host workloads, without treating the network as a trust boundary. | Infrastructure security | Aligns infrastructure security with Zero Trust principles by treating infrastructure as enforceable but not inherently trusted.
**Extended environment and non‑traditional asset support**<br/><br/>Explicitly recognizes IT/OT/IoT convergence and the need for Zero Trust capabilities across constrained and heterogeneous environments. | Infrastructure (OT/IoT security) | Matches adoption reality where OT/IoT require distinct ownership but must still align to enterprise Zero Trust strategy.
**Capability‑based maturity and continuous improvement**<br/><br/>Provides a capability model intended to assess current state, guide improvement, and adapt over time as threats and technology evolve. | Security posture | Positions Zero Trust as an ongoing program, not a one‑time deployment — aligning directly with posture management goals.

### Map Microsoft technologies to the model

The Zero Trust Reference model also includes an overall summary of Zero Trust components. This diagram shows how Microsoft technologies map to those components:

:::image type="content" source="./media/adoption-zero-trust-open-mapping.png" alt-text="Diagram showing Microsoft technologies mapped to The Open Group Zero Trust Reference Model components." lightbox="./media/adoption-zero-trust-open-mapping.png":::



## DoD Zero Trust Strategy

The US Department of Defense released a DoD Zero Trust Strategy and Roadmap.

For information on how to configure Microsoft cloud services for the DoD Zero Trust Strategy, see [Configure Microsoft services for the DoD Zero Trust strategy](dod-zero-trust-strategy-intro.md).

## What's next?

[Pick a business scenario](security-adoption-business-scenarios-overview.md) and learn how security disciplines map to the scenario.