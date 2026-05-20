---
title: Understand SecOps roles in the Microsoft security adoption model.
description: Understand Secops roles and responsbilities.
ms.date: 05/12/2026
ms.service: security
ms.subservice: zero-trust
author: rayne-wiselman
ms.author: raynew
ms.topic: conceptual

#customer intent: As a business leader or security adopter, I want to understand the roles and teams involved in SecOps.
---

# Understand SecOps roles

As you develop a [Security Operations (SecOps)](security-adoption-discipline-security-operations.md) discipline, this article explains the roles, responsibilities, and internal partnerships required to operate an effective, modern SecOps model aligned to Zero Trust principles.

SecOps is a specialized discipline focused on detecting, investigating, and responding to active threats in near real-time. It operates in continuous conflict with adversaries who actively adapt their techniques.

This guidance is intended for anyone planning or participating in SecOps modernization, including security leaders, SecOps practitioners, architects, engineers, and partner teams.

## Why roles and operating models matter

SecOps outcomes depend as much on people and collaboration as on technology. Even the most advanced detection and response tooling is ineffective without:

- Clear ownership during incidents
- Structured escalation paths
- Strong partnerships with teams that design, run, and understand the environment.

While SecOps is a dedicated security function, it relies heavily on the expertise of engineering, operations, and business teams that manage systems and processes across the organization.

A clear operating model ensures:

- Incidents are handled by the right roles at the right time
- Escalations are predictable and efficient
- Learnings from incidents translate into improved security posture

## SecOps roles and operating model 

These SecOps role definitions are based directly on The Open Group [Security Roles and Glossary Standard](https://publications.opengroup.org/s252), providing a common vocabulary and structure that scales from small teams to large, distributed SOCs.

In smaller organizations, these responsibilities may be combined into a few roles. In larger organizations, they are typically separated into specialized teams. Regardless of size, the functions and outcomes remain consistent.

SecOps roles and responsibilities are illustrated in this diagram:

:::image type="content" source="./media/security-adoption-discipline-operations-roles.png" alt-text="Diagram showing SecOps roles and responsibilities from The Open Group Security Roles and Glossary standard." lightbox="./media/security-adoption-discipline-operations-roles.png":::

In larger SecOps teams, specialized roles might be broken into dedicated teams. This diagram illustrates how these roles work together:

:::image type="content" source="./media/security-adoption-discipline-operations-roles-model.png" alt-text="Diagram showing SecOps roles organized into an operating model." lightbox="./media/security-adoption-discipline-operations-roles-model.png":::

## Core SecOps roles

- **Security Operations (SecOps) Manager**: Provides leadership and oversight for the SecOps function. Supports SecOps teams, aligns work to business priorities, and continuously improves effectiveness. 
- **Triage (Tier 1) Analyst**: Acts as the first responder for alerts and incidents. This role rapidly handles well‑understood attack patterns and escalates complex cases for deeper investigation.
- **Investigation (Tier 2) Analyst**: Leads response for complex or high‑impact incidents. This role investigates multi‑stage attacks, coordinates containment actions, and refines detection logic based on real incidents.
- **Threat Hunter (Tier 3)**: Proactively searches for attackers who have evaded detections. Threat hunters reduce attacker dwell time and contribute deep expertise during major incidents.
- **Detection Engineer**: Designs, tests, and improves detections to reduce blind spots. This role limits an attacker’s ability to operate undetected and improves detection and investigation procedures for analysts.
- **SecOps Platform and Data Engineer**: Ensures that SecOps tooling and data pipelines are reliable, scalable, and continuously evolving. This role underpins the effectiveness of all other SecOps functions.
- **Threat Intelligence Analyst**: Collects and analyzes threat information from internal and external sources and converts it into actionable insights for SecOps, security leadership, and partner teams.
- **Incident Coordination and Management**: Coordinates technical and business response during major incidents. This role manages communications, decision‑making, and cross‑functional execution during crises. 
- **Attack Simulation**: Tests organizational readiness through realistic simulations. Surfaces gaps across people, process, and technology. These simulations can take many forms and formats, including:
    - *Penetration testing* – simulation of a single operation to attempt compromise of an asset or the organization (often provided by an external organization).
    - *Red teaming* - simulation of persistent threat actor conducting multiple long-term operations.
    - *Purple teaming* – joint simulated attack operations where defenders (blue) and simulated attackers (red) work closely together to accelerate learning for both roles.
    - *Discussion-based simulation (tabletop exercise)* – structured simulation exercise for multiple roles to talk through a realistic attack scenario (sometimes supplemented by technical simulations).
- **Reverse Engineering/Digital Forensics (specialized roles)**: Highly specialized roles that analyze malware, artifacts, and evidence. Digital forensics specialists support legal and regulatory requirements by handling evidence with approved procedures and maintaining chain of custody.

## How SecOps roles work together

These roles operate as a layered model, where:

- Triage handles volume and speed
- Investigation and hunting handle complexity and depth
- Engineers improve the system continuously
- Leadership and coordination ensure alignment and resilience

This structure ensures scale without sacrificing quality.

## SecOps key internal partners

SecOps cannot operate effectively in isolation. Successful security operations depend on deep integration with teams that design, build, and operate the environment.

SecOps data and insights—especially threat intelligence—are most valuable when they inform prioritization decisions across the organization.

### Technical engineering/operations

These teams assist with investigation, containment, and recovery during incidents, and use SecOps insights to prioritize preventive controls.
Common partners include:

- Identity
- Network
- Endpoints
- Infrastructure and platforms (cloud, on‑premises, CI/CD)
- Data and AI
- Operational Technology (OT)

### Architecture roles

Architects design the systems SecOps monitors and defends, and incorporate lessons learned from incidents into future designs.

Key roles include:

 - Enterprise Architects
 - Security Architects
 - Infrastructure Architects
 - Data and AI Architects
 - Access Architects (identity, networks etc)
 - Solution Architects
 - Software and Application Architects

### Application and product development roles

These teams design and maintain the applications SecOps must detect and protect.

They support SecOps by:

- Assisting with investigation and remediation during incidents
- Ensuring applications generate appropriate telemetry
- Using SecOps intelligence to prioritize security improvements

## What's next?

Learn more about [security roles in the Open Group standard](https://publications.opengroup.org/standards/security/s252).

