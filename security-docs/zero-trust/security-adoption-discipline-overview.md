---
title: Overview - Security disciplines
description: Learn about security disciplines in the Microsoft security adoption model.
ms.date: 01/29/2026
ms.service: security
ms.subservice: zero-trust
author: MicrosoftGuyJFlo
ms.author: joflore
ms.topic: conceptual
#customer intent: As a business leader or security adopter, I want to understand which organizational disciplines are involved in planning, design, and deployment of business scenarios and outcomes.
---

# Overview - security disciplines

Security disciplines are groupings of related security work that help organizations plan, implement, and operate security consistently across their entire technology estate. 

Disciplines provide a structured way to translate business security goals and risk tolerance into coordinated technical implementation across the organization.

Rather than treating security as isolated controls or individual tools, security disciplines organize processes, skills, and technologies into repeatable capability areas. This helps ensure that security investments deliver measurable, end‑to‑end outcomes, not fragmented improvements.

Collectively, the security disciplines form a complete security operating model that enables:

- Clear security strategy and governance,
- Coherent, end‑to‑end architectures.
- Consistent technical implementation and operations.


> [!TIP]
> Microsoft offers a rich set of security adoption workshops - the *Security Adoption Framework (SAF) workshops*. Our structured adoption model, including security discipline guidance, that we describe here aligns with the expert-led guidance available in the workshops. Learn more about our [SAF workshops](workshop-business-overview.md).

## Security disciplines in adoption

In the adoption model, security disciplines provide an organizational structure between business scenarios and technical implementation.

- [**Business scenarios**](security-adoption-business-scenarios-overview.md)  define why security investment is needed and what outcomes matter.
- Security disciplines define who owns which areas of security work and how responsibilities are organized.
- Technical solutions and controls define how security is implemented using specific technologies.


## How to use security disciplines

Security disciplines are used throughout in our structured adoption model. They align to Zero Trust guidance to support different audiences:

- Business leaders and program owners use disciplines to understand coverage, accountability, and alignment to business risk.
- Security architects and planners use disciplines to shape end‑to‑end designs and ensure consistency across technology pillars.
- Implementation and operations teams use disciplines to guide tooling choices, control deployment, detection, and ongoing improvement.


The diagram below illustrates how security disciplines bridge business scenarios and outcomes on one side with technical platforms and operations on the other, providing a common structure for security decision‑making across the organization.

:::image type="content" source="./media/security-adoption-disciplines.png" alt-text="Diagram of security disciplines bridging technical work and business outcomes, organized by discipline type." lightbox="./media/security-adoption-disciplines.png":::


## Discipline categories

Each security discipline fits into one of three categories, based on the type of decisions it supports and when it is applied in the security lifecycle.

- **Planning and oversight disciplines**: These disciplines establish direction, alignment, and accountability across the entire security program. They define what success looks like and how progress is measured and governed.
- **Technical strategy disciplines**: These disciplines define how security is designed and implemented technically. They provide architectural direction that guides control selection, tooling, and execution across multiple technology areas.
- **Operational disciplines**: These disciplines define how security runs day to day, including continuous visibility, detection, response, and improvement as threats and environments change.

## Security disciplines

The following table shows the disciplines, the category they belong to, and the  technology pillars that they're focused on protecting.

**Disciplined/Category** | **Discipline** | **Pillar**
--- | --- | ---
[**Security strategy, integration, and governance**](security-adoption-discipline-strategy.md)<br/>Planning and oversight. | Establishes the overall security vision, priorities, policies and success measures. It ensures security efforts are aligned to business goals and risk tolerance, and that progress is measurable and governed. | All pillars.
[**End-to-end security architecture**](security-adoption-discipline-architecture.md)<br/>Planning and oversight. | Ensures that security controls, technologies, and processes work together as a cohesive system. It aligns architecture decisions across identity, data, applications, infrastructure, and operations to deliver consistent outcomes. | All pillars.
[**Access and identities**](security-adoption-discipline-identity-access.md)<br/>Technical strategy | Secures how users, devices, applications, and workloads access organizational assets. This discipline drives a consistent, identity‑centric approach across all access paths using Zero Trust principles. | Identity, networks, endpoints.
[**Infrastructure security**](security-adoption-discipline-infrastructure.md)<br/> Technical strategy | Detects the workloads and platforms that run the business, across hybrid and multicloud environments. This includes cloud services, on‑premises datacenters, | Infrastructure.
 **Dev security**](security-adoption-discipline-devops.md)<br/> Technical strategy | Ensures applications and services are designed, built, and maintained securely. This includes secure coding practices, application security testing, and integrating security into the development lifecycle. | Apps.
[**Data security**](security-adoption-discipline-data.md)<br/> Technical strategy | Protects data assets such as intellectual property, trade secrets, and regulated information. This discipline applies security controls throughout the full data lifecycle, regardless of where data is stored or how it moves. It is a critical enabler of safe Generative AI usage. | Data.
**OT/IoT security**<br/> Technical strategy | Secures OT/IoT systems that interact with physical processes and the physical world, including industrial control systems and SCADA environments. | Endpoints.
[**Security posture management**](security-adoption-discipline-posture.md)<br/>Operational | Continuously discovers, measures, and prioritizes security risks. It helps organizations focus remediation efforts on the most impactful vulnerabilities and attack paths. | All pillars.
[**SecOps**](security-adoption-discipline-security-operations.md)<br/>Operational  | Detects, responds to, and recovers from active threats. This discipline focuses on minimizing the time attackers have access after compromise, limiting realized business impact.| All pillars.


## What's next

- [Get started](security-adoption-model.md) with security adoption.
- [Select a business scenario](security-adoption-business-scenarios-overview.md).
- 

