---
title: Security adoption roles, responsibilities, and accountabilities
description: List of resources to read about Microsoft's Zero Trust framework
ms.author: raynew
author: rayne-wiselman
ms.topic: article
ms.service: security
ms.date: 04/27/2026

#customer intent: As a Microsoft security platform adopter, I want to understand the roles involved in security modernization and adoption.
---

# Review adoption roles and responsibilities

Adopting a Zero Trust security model is a strategic transformation that affects the entire organization, and  requires clear ownership and coordination across business, security, and technology teams. It's not a single technology deployment or a one-time project. Successful adoption depends on sustained leadership and the alignment of roles that plan, implement, and operationalize Zero Trust at scale.

This article describes the key organizational roles involved in Zero Trust adoption and explains how these roles work together to plan, implement, and operationalize Zero Trust at scale.

## Why roles matter in adoption

Zero Trust shifts security from a perimeter-based model to one that continuously verifies users, devices, applications, and data. This shift affects business processes, user experience, IT operations, and risk management.

Without clear roles and responsibilities:

- Security initiatives stall or fragment.
- Technology teams optimize locally instead of aligning to business and security priorities.
- Leaders lack visibility into security modernization progress and outcomes.

Defining role ownership helps translate Zero Trust strategy into coordinated action and measurable security improvements across the organization.

## Security is everyone's job

Security is fundamentally a human discipline that manages risk from human threat actors. While automation and AI play important roles, people remain central to security outcomes.


- Security is an intrinsic part of every business area. It has  fiduciary and risk implications, impacts business capabilities and execution, and all technologies.
- Security is everyone's job. From the board of directors to technology teams, non-technical teams such as finance and legal, and information/frontline workers.
- For effective security risk management, every person must understand security in the context of their role, and actively support security objectives.
- Since anyone in the organization can create or amplify security risk, everyone must apply security principles in their daily actions and decisions.

This diagram from the standard illustrates how to delegate security accountability and responsibility throughout an organization:

:::image type="content" source="./media/adoption-role-delegation.png" alt-text="Illustration of how to delegate security accountability and responsibility through an organization" lightbox="./media/adoption-role-delegation.png":::

### Security is a team sport

Managing security risk effectively requires accountability and collaboration:

- Collaboration between accountable and responsible parties is critical.
- Making good security decisions requires a healthy and relationship where accountable decision-makers and security experts can safely share ideas and challenge assumptions.

Following these tenets, security risk should be managed in a similar way to financial and legal risk. Each role has policies and education/training that guide their daily decisions, rather than assigning responsibility and even blame to security teams only.

:::image type="content" source="./media/adoption-role-collaboration.png" alt-text="Illustration of how accountable and responsible parties should collaborate" lightbox="./media/adoption-role-collaboration.png":::

## Role definition outcomes

When roles are clearly defined, aligned, and connected:

- Leadership sets priorities and accountability
- Business and risk functions align security to outcomes
- Architecture and technical leadership design scalable solutions
- Engineering and operations implement and sustain controls
- Security operations validate effectiveness
- Everyone participates in protecting the organization

Clear ownership and shared responsibility turn Zero Trust from an aspiration into a durable, measurable security strategy.

## Roles and terminology

Role terminology and definitions are based on the [Open Group Security Roles and Glossary Standard](https://publications.opengroup.org/s252). This diagram illustrates the list of roles.

:::image type="content" source="./media/adoption-role-list.png" alt-text="Illustration of security roles in the Microsoft Security Adoption Framework" lightbox="./media/adoption-role-list.png":::

### Organizational leadership and governance

**Purpose**: Set direction, provide authority, and ensure accountability.
Executive leadership establishes Zero Trust as an organizational priority and creates the conditions for long-term success.

**Responsibilities include**:

- Sponsor Zero Trust as a business and risk-management strategy
- Align security objectives with business goals, regulatory obligations, and risk tolerance
- Provide sustained funding, staffing, and organizational support
- Establish governance models and accountability structures
- Hold leaders responsible for measurable security outcomes

When leadership treats Zero Trust as a business enabler rather than a technical project, adoption gains momentum and durability.

### Business management and operations

**Purpose**:  Embed Zero Trust into day-to-day business execution.
Business leaders and operational managers ensure that Zero Trust supports productivity, customer trust, and operational resilience.

**Responsibilities include**:

- Integrate Zero Trust requirements into business processes and workflows
- Balance security controls with user experience and operational efficiency
- Identify critical business assets, processes, and data to prioritize protection
- Support change adoption across teams and functions
- Measure business impact of security decisions

Zero Trust succeeds when security enables business operations instead of being perceived as an obstacle.

### Security-adjacent leadership (CSO, CRO, CPO, compliance, audit)

**Purpose**: Align security strategy with enterprise risk, compliance, and protection objectives. These roles connect Zero Trust to broader enterprise risk management and assurance functions.

**Responsibilities include**:

- Translate Zero Trust principles into risk, compliance, and privacy requirements
- Ensure alignment with regulatory, legal, and industry obligations
- Validate controls through audit, assessment, and assurance activities
- Advise leadership on risk tradeoffs and residual risk
- Coordinate across security, compliance, and governance domains

Their involvement ensures Zero Trust is defensible, auditable, and aligned with organizational obligations.

### Other cross-functional disciplines (legal, finance, communications, PR)

**Purpose**: Enable Zero Trust adoption across non-technical dimensions.
Zero Trust impacts contracts, budgets, communications, and external trust.

**Responsibilities include**:

- Legal: supporting data protection, contracts, and regulatory interpretation
- Finance: funding models, cost governance, and investment prioritization
- Communications and PR: internal and external messaging during incidents or changes
- HR and people teams: policy enforcement, training alignment, and workforce engagement

These roles help ensure Zero Trust adoption is sustainable, compliant, and well-communicated.

### Technical leadership

**Purpose**: Translate strategy into executable technical direction.
Technical leaders bridge business intent and engineering execution.

**Responsibilities include**:

- Define technical priorities aligned to Zero Trust outcomes
- Coordinate across platforms, domains, and engineering teams
- Make tradeoff decisions between security, performance, and usability
- Ensure consistency across identity, endpoint, application, data, and infrastructure domains
- Support modernization of legacy systems

Strong technical leadership prevents siloed implementations and fragmented security posture.

### Architecture

**Purpose**: Design scalable, coherent Zero Trust solutions.
Security and enterprise architects ensure Zero Trust principles are applied consistently and sustainably.

**Responsibilities include**:

- Define target-state Zero Trust architectures
- Map Zero Trust concepts to platforms, services, and workloads
- Identify architectural gaps, dependencies, and integration points
- Provide design guidance and reference patterns
- Ensure solutions scale with business and technology change

Architecture turns principles into systems that can evolve over time.

### Application and product development

**Purpose**: Build Zero Trust into applications and services by design.
Development teams play a critical role in enforcing Zero Trust at the application layer.

**Responsibilities include**:

- Design applications that verify explicitly and enforce least privilege
- Integrate identity, access control, and data protection into applications
- Support secure APIs, service-to-service access, and workload identities
- Partner with security teams to reduce risk without harming velocity
- Address security early in the development lifecycle

Zero Trust is strongest when applications assume no implicit trust.

### Security strategy roles and responsibilities (insider risk, security education, compliance management)

**Purpose**: Shape long-term security behavior and maturity.
These roles focus on people, policy, and sustained security effectiveness.

**Responsibilities include**:

- Define security strategy, standards, and roadmaps
- Manage insider risk and user-related threats
- Drive security awareness, education, and culture
- Oversee security compliance and policy enforcement
- Measure maturity and progress against Zero Trust objectives

They ensure Zero Trust becomes embedded in how the organization operates, not just how it deploys technology.

### Technical engineering and operations

**Purpose**: Implement and operate Zero Trust controls.
Engineering and operations teams turn designs into functioning systems.

**Responsibilities include**:

- Deploy security controls across identity, devices, applications, data, and infrastructure
- Integrate security into operational workflows and platforms
- Manage change, testing, and roll out to minimize disruption
- Maintain system reliability, availability, and performance
- Continuously improve controls based on feedback and telemetry

These teams make Zero Trust real and reliable.

### Security operations (SecOps / SOC)

**Purpose**: Validate Zero Trust under real-world conditions.
Security operations teams close the loop between design and reality.

**Responsibilities include**:

- Monitor telemetry and signals across users, devices, and workloads
- Detect threats, policy violations, and anomalous behavior
- Respond to incidents and coordinating containment and recovery
- Feed operational insights back into policies, architecture, and automation
- Measure effectiveness through detection, response, and impact metrics

Zero Trust assumptions are tested and refined through daily operations.


## What's next?

- [Select a business scenario](security-adoption-business-scenarios-overview.md), and then review the disciplines and roles associated with the scenario. 
- Alternatively, review the [breadth of disciplines](security-adoption-discipline-overview.md) involved in security adoption.



