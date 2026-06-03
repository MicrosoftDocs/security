---
title: Zero Trust as a security foundation
description: Get an overview of core Zero Trust principles and how to use them in security adoption and modernization. 
ms.author: raynew
author: rayne-wiselman
ms.topic: article
ms.service: security
ms.subservice: zero-trust
ms.date: 05/24/2026

#customer intent: As a security business leader and adopter, I want to understand the Zero Trust principles that underline Microsoft's security adoption and implementation guidance.
---

# Zero Trust as a security foundation

This article provides an overview of core Zero Trust principles as a modern security foundation for designing, implementing, and operating security controls across your organization.

Zero Trust is a modern security approach based on a simple idea: **never trust, always verify**.

Access is granted only after we verify:

- Who is requesting access?
- What device are they using?
- What's their location and behavior?
- What's their risk level?

Verification doesn’t happen only once. It's continuous, ensuring that trust is maintained throughout a session.

## Zero Trust principles

Zero Trust is built on three principles that govern access decisions and security controls.

**Principle** | **Implementation**
--- | ---
**Verify explicitly** | Every access request is **authenticated and authorized using all available signals**.
**Use least privilege access** | User and workloads get **only the access they need, for the shortest time required**. 
**Assume breach** | Security controls are designed with the expectation that **attackers might be operating inside the environment**. Controls focus on limiting breach impact, and enabling rapid threat detection and response.


:::image type="content" source="./media/zero-trust-principles.png" alt-text="Diagram of Zero Trust security model highlighting the need to challenge traditional security assumptions." lightbox="./media/zero-trust-principles.png":::


## Zero Trust outcomes

When applied consistently, Zero Trust leads to clear, consistent, and measurable security outcomes that replace traditional "trust-by-default" models with "trust-by-exception".

- **Access is explicitly granted and continuously evaluated**: Trust isn't static. Every request is assessed in real time as conditions change.
- **Access is conditional and temporary**: Permissions are granted only when required and are removed when no longer valid.
- **Permissions are tightly scoped**: Users and workloads operate with the minimum access needed.
- **Security controls operate consistently**: Controls are consistently applied to  all environments, including on-premises systems, cloud platforms, SaaS applications, and AI workloads.
- **Detection and response are built-in**: Continuous monitoring provides faster threat identification, containment, remediation, and response.


## Challenging traditional assumptions 

Traditional security models rely on network boundaries, assume that assets inside the perimeter are safer than those outside, and see security as the responsibility of the security team.

While such models were effective against older threats such as network scanning and direct exploitation, they aren't sufficient today because modern attacks use identity compromise, phishing, and session hijacking, and aren't dependent on network location.

Zero Trust replaces this model by:

- Treating every **access request as untrusted regardless of origin**.
- Making decisions based on **real-time context**.
- Broadening **security responsibility**.

:::image type="content" source="./media/zero-trust-assumptions.png" alt-text="Diagram of Zero Trust security model highlighting the need to challenge traditional security assumptions." lightbox="./media/zero-trust-assumptions.png":::

## Key shifts

Key shifts to Zero Trust security mean that:

- **Protection follows the asset**
    Assets aren't inherently protected by where they reside. Every access request is explicitly validated, access to sensitive resources is tightly restricted, and activity is continuously monitored for threats.
- **Access is always validated and monitored**
    Security decisions are based on current conditions.
- **Security isn't only technology**
    People and processes introduce risk.
    - Human behavior such as using unauthorized data, credential sharing, lack of security hygiene, and other security shortcuts potentially introduce exposure that attackers exploit.
    - Processes such as system deployment, data sharing, and security control enforcement directly influence risk. 
- **Everyone shares in responsibility**
    We must recognize that security is everyone's job.
    - Continuous verification and least privilege help reduce the impact of human factors.
    - Security controls must align with real‑world usage and decision‑making.


## Structured adoption journey

Adopting Zero Trust security is a gradual, long‑term effort.

Every organization starts the journey from a different place, influenced by security maturity, existing technology, and risk profile.

A structured approach to adoption ensures that Zero Trust principles are applied consistently as security matures. Our structured adoption model focuses on three components:

- **Business scenarios**
    Help business leaders to define and prioritize security outcomes for the organization, focusing on the most critical areas of risk. 
- **Security disciplines**
    Guide teams to define strategy, architecture,  processes, and controls across common areas of security. Each business scenario usually maps to one or more security disciplines. 
- **Technology pillars**
    Focus on specific areas of security such as identity, data, and devices. Implementation guidance might be aimed at a specific business scenario, or might focus on a specific technology pillar.

:::image type="content" source="./media/zero-trust-principles-adoption.png" alt-text="Diagram of Zero Trust principles applied to security adoption, showing connections between business scenarios, security disciplines, and technology pillars." lightbox="./media/zero-trust-principles-adoption.png":::

## Next steps

- To get started with structured adoption, follow our [Zero Trust adoption path](security-adoption-model.md).
- To dive into critical security outcomes, start with our [business scenarios](security-adoption-business-scenarios-overview.md).
- To begin with assessment of your current Zero Trust posture, start [Zero Trust assessment](assessment/overview.md).
To dive directly into implementation, review [implementing technical solutions](implement-overview.md).



