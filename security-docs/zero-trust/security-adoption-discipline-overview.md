---
title: Overview - Security disciplines
description: Learn about security disciplines in the Microsoft security adoption model.
ms.date: 05/24/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual
#customer intent: As a business leader or security adopter, I want to understand which organizational disciplines are involved in planning, design, and deployment of business scenarios and outcomes.
---

# Overview - security disciplines

This article provides an overview of security disciplines in the [Microsoft security adoption model](security-adoption-model.md).

Security disciplines are **structured areas of accountability** that help organizations translate business security goals into coordinated action across the enterprise. They provide a consistent way to organize strategy, architecture, and operations to manage risk and protect critical business outcomes.

Rather than treating security as isolated controls or individual tools, security disciplines organize processes, skills, and technologies into repeatable capability areas. This helps ensure that security investments deliver measurable, end‑to‑end outcomes, not fragmented improvements.

Collectively, the security disciplines form a complete security operating model that enables:

- Clear security strategy and governance,
- Coherent, end‑to‑end architectures.
- Consistent technical implementation and operations.

Security disciplines are applied through business scenarios, such as securing remote work or protecting critical assets. These scenarios define where security efforts should be focused to reduce risk and support the business.

> [!TIP]
> Microsoft offers a rich set of security adoption workshops - the *Security Adoption Framework (SAF) workshops*. Our structured adoption model, including security discipline guidance, that we describe here aligns with the expert-led guidance available in the workshops. Learn more about our [SAF workshops](workshop-business-overview.md).

## Security disciplines in adoption

In our [security adoption model](security-adoption-model.md), security disciplines provide an organizational structure between business scenarios and technical implementation.

- [**Business scenarios**](security-adoption-business-scenarios-overview.md)  define **why** security investment is needed and what outcomes matter.
- Security disciplines define ownership and accountability across teams, clarifying **who** is responsible for delivering each area of security capability across the organization.
- [Technical solutions](implement-overview.md) define **how** security is implemented across specific [technology pillars](deploy/overview.md).

:::image type="content" source="./media/disciplines.png" alt-text="Diagram showing how disciplines bridge business outcomes and technical implementation, organized by discipline type." lightbox="./media/disciplines.png":::

## How to use security disciplines

Security disciplines are used throughout in our structured adoption model. They align to Zero Trust guidance to support different audiences:

- Business leaders and program owners use disciplines to understand how security business scenarios come to life to protect assets and manage business risk. 
- Security leaders and architects use disciplines to shape end‑to‑end designs and ensure consistency across technology pillars.
- Implementation and operations teams use disciplines to guide tooling choices, control deployment, detection, and ongoing improvement.



## Discipline categories

Each security discipline fits into one of three categories, based on the type of decisions it supports and when it is applied in the security lifecycle.

- **Planning and oversight disciplines**: These disciplines establish direction, alignment, and accountability across the entire security program. They define what success looks like and how progress is measured and governed.
- **Technical strategy disciplines**: These disciplines define how security is designed and implemented technically. They provide architectural direction that guides control selection, tooling, and execution across multiple technology areas.
- **Operational disciplines**: These disciplines define how security runs day to day, including continuous visibility, detection, response, and improvement as threats and environments change.


The diagram below illustrates how security categories and disciplines, and how they align across technology pillars.

:::image type="content" source="./media/security-adoption-disciplines.png" alt-text="Diagram of security disciplines guiding security adoption." lightbox="./media/security-adoption-disciplines.png":::

## Security disciplines

The following table shows the disciplines, the category they belong to, and the  technology pillars that they're focused on protecting.

**Disciplined/Category** | **Discipline** | **Pillar**
--- | --- | ---
**[Security Strategy, Integration, and Governance](security-adoption-discipline-strategy.md)**<br/>Planning and oversight. | Establishes the overall security vision, priorities, policies and success measures. It ensures security efforts are aligned to business goals and risk tolerance, and that progress is measurable and governed. | All pillars.
**[Security Architecture](security-adoption-discipline-architecture.md)**<br/>Planning and oversight. | Ensures that security controls, technologies, and processes work together as a cohesive system. It aligns architecture decisions across identity, data, applications, infrastructure, and operations to deliver consistent outcomes. | All pillars.
**[Access and Identity](security-adoption-discipline-identity-access.md)**<br/>Technical strategy | Secures how users, devices, applications, and workloads access organizational assets. This discipline drives a consistent, identity‑centric approach using Zero Trust principles across all access paths, including networking and privileged access. | Identity, networks, endpoints.
**[Infrastructure Security](security-adoption-discipline-infrastructure.md)**<br/> Technical strategy | Ensures that the workloads and platforms that run the business are secure across hybrid and multicloud environments for new development and legacy apps.  | Infrastructure.
**[Development Security](security-adoption-discipline-development.md)**<br/> Technical strategy | Ensures applications and services are designed, built, and maintained securely as pat of a DevSecOps approach and a security development lifecycle (SDL). This includes secure coding practices, and application security testing. | Apps.
**[Data Security](security-adoption-discipline-data.md)**<br/> Technical strategy | Protects data assets such as intellectual property, trade secrets, and regulated information. This discipline applies security controls throughout the full data lifecycle, regardless of where data is stored or how it moves. It is a critical enabler of safe Generative AI usage. | Data.
**[OT/IoT Security](security-adoption-discipline-iot.md)**<br/> Technical strategy | Secures OT/IoT systems that interact with physical processes and the physical world, including industrial control systems and SCADA environments. | Endpoints.
**[Security Posture Management](security-adoption-discipline-posture.md)**<br/>Operational | Continuously discovers, measures, and prioritizes security risks. It helps organizations focus remediation efforts on the most impactful vulnerabilities and attack paths. | All pillars.
**[SecOps](security-adoption-discipline-security-operations.md)**<br/> Operational  | Detects, responds to, and recovers from active threats. This discipline focuses on rapid response, to minimize the time attackers have access after compromise, and thus limiting their business impact. | All pillars.


## Next steps

- [Get started](security-adoption-model.md) with security adoption.
- [Select a business scenario](security-adoption-business-scenarios-overview.md).
- [Learn about Microsoft's security workshops](workshop-business-overview.md)

