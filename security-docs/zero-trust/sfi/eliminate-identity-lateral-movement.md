---
title: Eliminate identity lateral movement – Zero Trust
description: Eliminate identity lateral movement is part of the protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI), focusing on minimizing the potential impact of security incidents through strong tenant isolation, segmentation, and attack surface reduction. 
ms.date: 08/05/2025
ms.service: security
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Eliminate identity lateral movement (Secure Future Initiative)

**Pillar name: Protect tenants and isolate production systems**<br>
**Pattern name: Eliminate identity lateral movement**

Eliminate identity lateral movement is a core focus of the protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI). This pillar focuses on minimizing the potential impact of security incidents through strong tenant isolation, segmentation, and attack surface reduction.

## Context and problem

Identity lateral movement is a tactic threat actors use to exploit compromised credentials to pivot across systems and elevate privileges. Unlike brute-force attacks or malware-based exploits, identity-based lateral movement can blend in with legitimate user behavior, making it difficult to detect and even harder to stop without strong access to governance.

Recent attacks—such as the Midnight Blizzard—demonstrated how lateral movement can be enabled through overlooked accounts, external guest access, or pivot points created by multitenant Entra applications. These scenarios bypass traditional defenses and allow threat actors to move across organizational boundaries.

Once inside, attackers often:

- Target privileged accounts to escalate access

- Move between tenants or services using shared credentials

- Abuse application permissions or misconfigured roles

- Remain undetected by mimicking normal tenant behavior

## Solution

Combined, the following efforts prevent compromised accounts or applications from becoming springboards for lateral movement within or between tenants:

- Creating a tenant layering standard that allows Microsoft to categorize tenants into layers and define the valid direction for service principal creation.

- Moving customer support workflows and scenarios into a dedicated tenant to reduce the risk of lateral movement.

- Moving off legacy authentication protocols and instead enforce phishing-resistant MFA for all users, including guest accounts.

- Segmenting access by device compliance, location, and risk level using conditional access policies.

- Enforcing least privilege with role-based access controls (RBAC) and time-bound role assignment.

- Replacing password-based application credentials with managed identities and secure key storage.

- Blocking all but explicitly approved external guest user authentication requests to sensitive Entra applications.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Strengthen authentication  | <ul><li>Require phishing-resistant MFA for all users, including guests </li><li>Block legacy authentication and enforce Conditional Access policies</li><li>Monitor the dark web for credential leaks and enforce password hygiene for users</li></ul>|[Microsoft Entra Conditional Access documentation](/entra/identity/conditional-access/) |
| Control privileged access |<ul><li>Use Microsoft Entra Privileged Identity Management (PIM) to enforce just-in-time and just-enough access </li><li>Implement Secure Admin Workstations (SAWs) to separate admin activity from daily use </li><li>Limit admin roles to specific apps, groups, or tenants using Restricted Management Administrative Units (RMAU)</li></ul>| [What is Microsoft Entra Privileged Identity Management?](/entra/id-governance/privileged-identity-management/pim-configure)  |
| Segment environments |<ul><li>Separate production and non-production environments at the tenant and device level</li><li>Apply network segmentation in Azure using VNets, subnets, and Network Security Groups (NSGs)</li><li>Enforce identity context–based policies for resource access</li></ul>| [Azure network security groups overview](/azure/virtual-network/network-security-groups-overview)|
| Mitigate pivot points |<ul><li>Prefer single-tenant app registrations when cross-tenant access is unnecessary </li><li>Review and restrict access for multitenant applications and service principals </li><li>Disable Entra All Users group and apply Access Reviews to clean up guest accounts</li></ul>| <ul><li><a href="/entra/id-governance/access-reviews-overview">What are access reviews?</a></li><li><a href="/entra/id-governance/">Microsoft Entra ID Governance documentation</a></li></ul> |
| Monitor and detect movement |<ul><li>Use Microsoft Sentinel to detect anomalous privilege escalation, file access, or identity behavior </li><li>Integrate Entra ID risk signals and user behavior analytics for early threat detection </li><li>Set up alerting for external app consents, dormant accounts, and sudden privilege changes</li>| [Microsoft Sentinel documentation](/azure/sentinel/) |

## Outcomes

### Benefits

- **Reduced pivot paths:** Guest users and multitenant apps are tightly scoped and actively monitored.

- **Stronger privileged access management:** Admin accounts operate in secure contexts (e.g., Secure Admin Workstations).

- **Improved detection:** Identify and monitor behavioral anomalies and high-risk events.

- **Policy-driven control:** Conditional Access and identity governance tools enforce identity separation and activity boundaries.

### Trade-offs

Implementation requires:

- Coordination across multiple security and identity teams to apply Conditional Access and app controls

- Enforcement of stricter authentication policies, which impacted guest access and collaboration workflows

- Migration from legacy applications that use passwords or weak secrets

- Investment in governance tools to automate reviews and lifecycle management for applications, users, and guest access

## Key success factors

Monitor the following KPIs:

- Reduction in guest users with elevated or group access

- Number of active Conditional Access policies applied to applications and admin roles

- MFA coverage across all identity types

- Frequency of identity-related incident response events

- Percentage of privileged actions originating from secure, segmented devices

- Volume of cross-tenant authentication attempts blocked

## Summary

When threat actors can move laterally across the network, they can access sensitive digital assets, breach data, and disrupt operations. Using stolen credentials, they can elevate their privileges and manipulate backend systems for malicious purposes. This kind of  lateral movement is difficult to detect because it looks like standard user behavior.

**Begin eliminating the pathways for identity lateral movement today—and secure every access path, application, and account against silent intrusions.**
