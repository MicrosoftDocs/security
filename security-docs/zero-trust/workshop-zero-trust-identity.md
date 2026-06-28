---
title: Microsoft Zero Trust Workshop - Identity
description: Learn about the Identity pillar in the Microsoft Zero Trust Workshop
ms.date: 05/31/2026
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: concept-article

#customer intent: As a security implementer, I want to understand how the Identity Security Zero Trust workshop can help with identity deployment that's aligned with Zero Trust principles and security best practices.
---

# Identity in the Microsoft Zero Trust Workshop

In a Zero Trust framework, identity is the foundational control plane. Every access decision to a device, application, or data resource begins with verifying who the user is, what their privileges are, and whether their context meets policy.

The Identity pillar in the Zero Trust Workshop ensures that organizations align with Zero Trust principles (verify explicitly, enforce least privilege, and assume breach) across all identities. It provides a **prioritized and actionable implementation backlog** for modernizing identity capabilities.

Identity pillar workshop guidance focuses on assessing your current identity posture, identifying gaps, and defining prioritized actions to modernize identity controls, reduce risk, and enable secure, seamless access across your environment.

## Workshop implementation

The Identity workshop covers the implementation areas summarized in the table.


**Area** | **Details**
--- | ---
**Inventory and understand identity assets**  | Compile a complete inventory of users, applications, service principals, groups, and identity attributes.<br/><br/>Assign ownership, define accountability, and classify critical identity assets to establish governance and visibility across the identity estate.
**Establish a strong Conditional Access foundation**  | Implement a comprehensive Conditional Access strategy that continuously evaluates identity, device state, risk signals, and session context.<br/><br/> Define and enforce consistent access policies across users, applications, and scenarios, including workforce, guests, and legacy access paths.
**Modernize authentication and eliminate legacy protocols**  | Standardize on modern authentication across all applications and services.<br/><br/>Eliminate legacy authentication methods and migrate existing systems to secure, standards-based authentication protocols to reduce exposure to credential-based attacks.
**Transform application and identity infrastructure**  |  Reduce dependency on on-premises identity systems by migrating applications to Microsoft Entra ID-based authentication and single sign-on (SSO).<br/><br/> Decommission legacy federation and web access management infrastructure.<br/><br/>Modernize application access patterns to support Zero Trust.
**Enforce least privilege and role-based access**  |   Assign access based on job function using role-based access control (RBAC) and access packages.<br/><br/> Define role models, enforce least privilege, and continuously validate access through access reviews and policy-based governance to ensure users only have the permissions they require.
**Protect privileged and workload identities**  |  Secure administrative and high-risk accounts using just-in-time access, Privileged Identity Management (PIM), strong authentication, and hardened access paths.<br/><br/>Extend governance and protections to workload identities and service principals to reduce risk from overprivileged or unmanaged identities.
**Establish identity data governance and provisioning flows** |   Define authoritative identity data sources, attribute schemas, and data flows across systems.<br/><br/> Implement provisioning pipelines and connectors to ensure identity data is consistent, accurate, and reliably synchronized across applications and services.
**Automate identity lifecycle and provisioning**  |  Implement automated provisioning and lifecycle workflows (joiner, mover, leaver) across authoritative systems such as HR platforms.<br/><br/> Ensure access is granted, updated, and removed automatically based on lifecycle events, with monitoring and validation of provisioning processes.
**Strengthen credential security with passwordless authentication** |   Reduce reliance on passwords by implementing password protection and deploying phishing-resistant, passwordless authentication methods such as FIDO2, Windows Hello for Business, and Microsoft Authenticator.<br/><br/> Drive adoption of strong authentication methods across the organization.
**Govern external and partner identities**  |  Establish controlled onboarding, access assignment, and lifecycle processes for external users and partner organizations.<br/><br/> Implement access packages, sponsorship models, and monitoring to ensure external identities are properly governed and aligned with organizational policy.
**Clean up and remediate existing access**  |  Identify and remediate overprivileged accounts, unused identities, and stale group memberships.<br/><br/>Conduct access reviews and implement ongoing governance processes to maintain least privilege and reduce accumulated identity risk over time.
**Enable identity security monitoring and response (SecOps)** | Integrate identity signals into security operations by incorporating identity protection, threat detection, and centralized logging.<br/><br/> Monitor identity health, detect suspicious activity, and investigate and respond to identity-based threats using security analytics and operational playbooks.


## Assess identity

The Zero Trust Assessment tool  can assess your identity configuration against a range of security best practices. [Learn more](/security/zero-trust/assessment/overview).

## Next steps

[Run an assessment](assessment/get-started.md), and begin the [Identity workshop](https://zerotrust.microsoft.com/).