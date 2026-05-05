---
title: Zero Trust as a security foundation
description: Get an overview of core Zero Trust principles and how to use them in security adoption and modernization. 
ms.author: raynew
author: rayne-wiselman
ms.topic: article
ms.service: security
ms.subservice: zero-trust
ms.date: 04/05/2026

#customer intent: As a security business leader and adopter, I want to understand the Zero Trust principles that underline Microsoft's security adoption and implementation guidance.
---

# Zero Trust as a security foundation

This article provides an overview of core Zero Trust principles as a modern security foundation for designing, implementing, and operating security controls across your organization.

Zero Trust is a modern security approach based on a simple idea: **never trust, always verify**.

Access is granted only after verifying:

- Who is requesting access?
- What device they are using?
- What's their location and behavior?
- What's their risk level?

This verification doesn’t happen once. It is continuous, ensuring that trust is maintained throughout the session.


## Zero Trust principles

Zero Trust is built on three principles that govern access decisions and security controls.

**Principle** | **Implementation**
--- | ---
**Verify explicitly** | Every access request is **authenticated and authorized using all available signals**.
**Use least privilege access** | User and workloads get **only the access they need**, for the **shortest time required**. This reduces risk and limits potential misuse.
**Assume breach** | Security controls are design with the expectation that attackers might already be inside the environment. Controls focus on limiting impact and enabling rapid threat detection and response.

## Zero Trust outcomes

When applied consistently, Zero Trust leads to clear, consistent, and measurable security outcomes that replace traditional "trust-by-default" models with "trust-by-exception", with access granted after validation and continuously reevaluated.

- **Access decisions are explicitly granted and continuously evaluated**: Trust isn't static. Every request is assessed in real time as conditions change.
- **Access is conditional and temporary**: Permissions are granted only when required and are removed when no longer valid.
- **Permissions are tightly scoped**: Users and workloads operate with the minimum access needed.
- **Security controls operate across all environments**: Controls apply consistently to on-premises systems, cloud platforms, SaaS applications, and AI workloads.
- **Detection and response are built-in**: Continuous monitoring is integrated for faster threat identification, containment, and remediation.


## Challenging traditional assumptions 

Traditional security models rely on network boundaries, assuming that assets inside the perimeter are safer than those outside.

While these models were effective against threats such as network scanning and direct exploitation, they're insufficient because modern attacks:

- Don't depend on network location.
- Use identity compromise, phishing, and session hijacking.  

Zero Trust replaces this model by:

- Treating every **access request as untrusted regardless of origin**.
- Making decisions based on **real-time context**.

:::image type="content" source="./media/zero-trust-assumptions.png" alt-text="Diagram of Zero Trust security model highlighting the need to challenge traditional security assumptions." lightbox="./media/zero-trust-assumptions.png":::

Key shifts to Zero Trust security mean that:

- **Protection follows the asset**: Assets aren't inherently protected by where they reside. Every access request is explicitly validated, access to sensitive resources is tightly restricted, and activity is continuously monitored for threats.
- **Access is always validated and monitored**: Security decisions are based on current conditions.
- **Security isn't just technology**: People and processes introduce risk. Human behavior (unauthorized data/credential sharing, insufficient security hygiene, shortcuts/tradeoffs) can introduce exposure that attackers exploit. Processes such as system deployment, data sharing, and security control enforcement directly influence risk. 


We must recognize that security is everyone's job. Continuous verification and least privilege reduce the impact of human factors, while aligning security controls with real‑world usage and decision‑making.


## Zero Trust adoption journey

Adopting Zero Trust is a gradual, long‑term effort. Every organization starts the journey from a different place, dependent upon security maturity, existing technology, and risk profile.

A structured approach to Zero Trust security adoption ensures that Zero Trust principles are applied consistently as security matures, and focuses on three areas:

- **Business scenarios** help business leaders to define and prioritize security outcomes for the organization, focusing on the most critical areas of risk. 
- **Security disciplines** guide teams to define strategy, architecture,  processes, and controls across common areas of security. Each business scenario usually maps to one or more security disciplines. 
- **Technology pillars** focus on specific areas of security such as identity, data, and devices. Implementation guidance for technology pillars helps technical teams with end-to-end implementation of business scenarios.

:::image type="content" source="./media/zero-trust-principles-adoption.png" alt-text="Diagram of Zero Trust principles applied to security adoption, showing connections between business scenarios, security disciplines, and technology pillars." lightbox="./media/zero-trust-principles-adoption.png":::

## What's next?

- To begin by assessing your current Zero Trust posture, start [Zero Trust assessment](assessment/overview.md).
- To get started with structured adoption, follow our [Zero Trust adoption path](security-adoption-model.md).
- To dive into critical security outcomes that business leaders might want to focus on, start with our [business scenarios](security-adoption-business-scenarios-overview.md).
To start directly with security implementation for business solutions and technical pillars such as devices and data, review [implementing technical solutions](implement-overview.md).






