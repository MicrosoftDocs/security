---
title: Establish a Security Posture discipline
description: Use the Microsoft security adoption model to optimize security posture across the business, based on Zero Trust principles.
ms.date: 05/12/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand how I can use the Microsoft security adoption model to optimize security posture across the business.
---

# Establish a Security Posture discipline

This article helps security and technology leaders establish or modernize a Security Posture Management discipline. This discipline focuses on continuously reducing the organizational exposure to attacks by identifying and eliminating the most likely attack paths to critical assets.

[Security disciplines](security-adoption-discipline-overview.md) are groupings of related security work that help organizations consistently deliver security outcomes across the entire technology estate. Within the security adoption model, disciplines help provide a bridge between [business scenarios](security-adoption-business-scenarios-overview.md) and [technical implementation](implement-overview.md), ensuring that security investments translate into real measurable outcomes as part of the [security adoption model](security-adoption-model.md).


## Why this discipline

Most successful cyberattacks don’t begin with advanced exploits. They start by abusing well-known, easily exploitable weaknesses—often in identity, endpoints, infrastructure, applications, or configuration hygiene.

The Security Posture discipline exists to prevent attacks before they occur, complementing the Security Operations (SecOps) discipline, which focuses on detection, investigation, and response after compromise.

- Security Posture reduces opportunity for attackers.
- Security Operations limits impact when prevention fails.

Together, they form a complete security operating model.

Without a dedicated Security Posture discipline, organizations often treat posture management as:

- A periodic vulnerability scan.
- A compliance checkbox.
- A collection of disconnected remediation projects.

This approach leaves systemic weaknesses in place until attackers exploit them. 

This diagram illustrates the complementary nature of Security Posture Management and Security Operations:

:::image type="content" source="./media/security-adoption-discipline-posture.png" alt-text="Diagram showing Security Posture Management focuses on preventing attacks (left of bang) while Security Operations manages incidents that occur (right of bang)." lightbox="./media/security-adoption-discipline-posture.png":::




## Mission and outcomes

Reduce the likelihood and impact of cyberattacks by continuously identifying and eliminating the most exploitable risks across the organization’s technology estate.

Organizations that mature this discipline achieve:

- Continuous discovery of assets across the modern estate.
- Prioritized visibility into exploitable vulnerabilities and attack paths.
- Faster, more effective remediation by asset-owning teams.
- Reduce attack surface and blast radius.
- Improved resilience against business disruption.

Security posture acts as the operational extension of governance, translating enterprise risk priorities into day-to-day remediation work.


## How to apply this discipline

To apply the Security Posture Management discipline effectively, focus on establishing a continuous, risk-driven approach to understanding and improving your organization’s security posture:

- **Define a posture management strategy aligned to business risk**  
  Establish a clear approach for identifying, measuring, and prioritizing security risks based on their potential impact on the business.

- **Ensure continuous visibility across the environment**  
  Maintain an up-to-date understanding of assets, configurations, and exposures across identities, devices, applications, infrastructure, and data.

- **Standardize how security risks are assessed and prioritized**  
  Provide clear guidance to ensure that vulnerabilities, misconfigurations, and risks are evaluated consistently and addressed based on impact.

- **Align posture management with business priorities and critical assets**  
  Focus remediation efforts on the most important risks affecting high-value assets and key business scenarios.

- **Continuously improve posture through measurement and remediation**  
  Use insights from assessments, risk trends, and remediation efforts to reduce exposure and strengthen security over time.


## Manage change

Modern Security Posture management represents a shift from static vulnerability reporting to continuous risk reduction.

**Tradional approach** | **Modern discipline**
--- | ---
Periodic vulnerability scans | Continuous asset and risk discovery.
Compliance-driven prioritization | Threat-informed prioritization.
Security-owned findings | Shared accountability with engineering teams and business owners of systems.
One-time remediation | Continuous remediation and improvement.
Patch by exception | Patch by default.



The following diagram shows the key elements of the Security Posture discipline.

:::image type="content" source="./media/security-adoption-discipline-posture-mission.png" alt-text="Diagram showing Security Posture Management mission with key elements: continuously discover assets, identify and prioritize vulnerabilities, and enable mitigation." lightbox="./media/security-adoption-discipline-posture-mission.png":::

### Key principles

Key modernization principles include:

- **Enablement**: Go beyond tools and reports. Equip engineering and operations teams with guidance, context, automation, and education to reduce risk as part of their normal work.
- **Scope**: Address weaknesses across multiple dimensions:
    - **Functional** - Address Design and implementation flaws.
   - **Configuration** -Address misconfiguration and configuration drift over time.
   - **Operational** - Address administrative and operational practices that enable abuse (for example, weak credential handling).
- **Operations**: Make posture improvement a continuous engineering activity—not a one-time cleanup. This requires sustained collaboration, cultural change, and incremental progress.

This discipline requires cultural change, sustained collaboration, and incremental improvement rather than one-time remediation projects.

## Security posture strategy 

An effective security posture strategy focuses on three continuous activities:

1. **Discover assets**: Continuously identify assets across the entire modern estate, including:
    - Identity systems
    - Endpoints
    - SaaS applications
    - Cloud and on-premises infrastructure
    - OT, IoT, and emerging platforms

    This requires close collaboration with asset ownership, configuration, and platform teams.
1. **Identify and prioritize exploitable risk**: Focus on vulnerabilities and attack paths that are:
    - Cheap for attackers to exploit.
    - Reliable at scale.
    - Common entry points for multistage attacks.

    Threat intelligence and real-world attack patterns should inform prioritization—not severity scores alone.

1. **Enable mitigation**: work with asset-owning teams to:
    - Integrate remediation into existing workflows. 
    - Reduce friction and repeat effort.
    - Track progress against risk reduction goals.

    Security Posture succeeds when remediation becomes faster and easier than ignoring risk.
 
## Discipline roles and collaborators

Security Posture is inherently cross-functional.

Primary roles include:

- **Engineering and Operations teams**:  Technology and Security Managers, Security and Automation Engineers accountable for implementing mitigations and maintaining hygiene across:
   - Identity and access
   - Networking
   - Endpoints and user productivity
   - Infrastructure and platforms (cloud, on-premises, CI/CD)
   - Data
   - AI
   - OT environments


- **Architecture Roles**: Design the systems and controls the Security Posture discipline monitors and improves:
   - Enterprise Architect
   - Security Architect
   - Infrastructure, identity, application, data, and AI architects.
   - Data and Artificial Intelligence (AI) architects.

- **Security Strategy, Integration, & Governance (All Others)**: Provide direction and support through:

    - Risk prioritization and metrics
    - Compliance and policy alignment
    - Security education and engagement

- **Threat Intelligence and SecOps**: Inform prioritization based on attacker behavior, active campaigns, and emerging techniques.


## Alignment with other disciplines

Security Posture Management works closely with other disciplines:

- **SecOps**: Prevention complements detection and response.
- **Security Strategy, Integration, and Governance**: Risk prioritization and metrics.
- **Security Architecture**: Consistent control placement.
- **Access and Identities**: Reducing identity-based attack paths.
- **Infrastructure**, **Development**, and **Data Security**: Eliminating systemic weaknesses.

Together, these disciplines create a cohesive security operating model.


## Alignment with technology pillars

Security Posture spans all technology pillars:

- **Identities** – This pillar is a top-priority for security posture because identity is a High-risk entry point that's foundational to nearly all attacks. Almost all multistage attacks rely on identity attacks, such as pass-the-hash, ticket, and other methods, to laterally traverse and gain access to additional organizational assets. These attacks often use privileged accounts associated with IT administrators or administrative service accounts.
- **Endpoints**: Endpoints are a common attacker foothold and staging environment. It's critical to quickly find and fix endpoint vulnerabilities.
- **Infrastructure**:  Rapidly finding and mitigating infrastructure vulnerabilities is important since infrastructure has broad impact due to shared dependencies for hosted workloads and data. 
- **Apps** | Rapidly finding and mitigating these vulnerabilities is important because threat actors often target email, collaboration, line of business, and other apps to enter and laterally traverse across an organization to access business assets.
- **Data** | Data provides a high-value target for theft, extortion, and disruption. Attackers often target data for intellectual property theft, encryption to gain leverage for extortion or ransomware, planning future attacks, and other purposes.
- **Networks**: Threat actors attack operations that rely on network connectivity. Network security conotrols restrict communication paths, constrain attacker movement and detect abnormal flows.
- **AI** | Emerging AI attack surfaces require new discovery and protection capabilities.

The discipline builds consistent skills, tooling, and processes across all pillars.

## What's next?

Microsoft Unified offers expert-led workshops to help organizations accelerate modernization of Security Posture Management strategy, architecture, and technology. These workshops include:

- **Architecture and strategy workshops** - The Security Adoption Framework (SAF) – Chief Information Security Officer (CISO) Workshop* workshop covers security posture management as part of a modern and effective security strategy and program. 
- **Technology adoption workshops** - The *Onboarding Accelerator - Microsoft Security Exposure Management* engagement accelerates adoption of Microsoft Security Exposure Management. 

Contact your customer success account manager for more information on Microsoft-led workshops.


