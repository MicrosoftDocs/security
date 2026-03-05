---
title: Remove legacy systems that risk security – Zero Trust
description: Remove legacy systems that risk security is part of the protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI), focusing on removing legacy and unmanaged tenants to reduce Microsoft’s attack surface.
ms.date: 03/05/2026
ms.service: security
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Remove legacy systems that risk security (SFI)

**Pillar name: Protect tenants and isolate production systems**<br>
**Pattern name: Remove legacy systems that risk security**

## Context and problem

Modern threat actors actively target unmanaged, legacy, or employee-created tenants that lack modern security controls. These tenants often:

- Operate outside centralized governance
- Lack strong authentication, Conditional Access, and compliance enforcement
- Introduce configuration drift and lateral movement paths
- Persist well past their intended purpose (e.g., abandoned test/demo environments)

In production environments, these risks are amplified. A single compromised legacy tenant can be used as a launchpad for broader attacks, undermining Zero Trust principles and exposing sensitive systems. Real-world incidents have included password spray against nonproduction tenants and abuse of legacy test apps to pivot into corporate environments.

Tenant sprawl inflates attack surface, complicates governance, and slows incident response. Reducing and governing the tenant footprint is one of the highest leverage security investments most enterprises can make.

## Solution

Microsoft implemented a comprehensive cleanup and segmentation initiative under the Secure Future Initiative (SFI) to eliminate legacy and unmanaged tenants, while hardening the remaining estate. Key actions included:

- **Discovery and cleanup at scale**: Comprehensive inventory across the Microsoft cloud footprint and removal of millions of unused or insecure tenants via automated workflows and time‑bound scream tests. Microsoft removed 6.9 million unused and aged tenants as of November 2025.
- **Segmentation and hardening**: Clear classification of tenants (Primary production environments, Additional production environments, and Temporary non-production environments), Conditional Access enforcement, logical isolation, and secure‑by‑default baselines.
- **Tenant lifecycle policy**: Automated creation guardrails and 90‑day expiration for non‑production/ephemeral tenants, with extensions requiring deputy CISO approval.
- **Modernization**: Migration of legacy platforms (e.g., ASM → ARM), secrets hygiene (managed identities, Key Vault), and elimination of shared secrets.
- **Governed creation**: Policy‑driven tenant creation with approval workflows and attribution; default block by default cross‑tenant trust

## How does Microsoft classify their tenants?

To make risk explicit and controls predictable, Microsoft internal tenants are scoped by persona, business purpose, and risk profile. 

The resulting classifications are summarized in the following table.

| **Class** | **Examples** | **Lifecycle** | **Cross‑tenant  posture** | **Typical controls** |
| --- | --- | --- | --- | --- |
| **Primary production  environments** (core tenants)<br/><br/>Primary production and productivity tenants that run Microsofts most critical services and operations. Tightly governed with the highest security standards.| Microsofts main productivity environment  supporting daily operations for our workforce <br/><br/>Environment running Microsofts cloud services for our customers. | Long‑lived | Strict, minimal exceptions | Strong auth only (FIDO2/Auth App)<br/>JIT  elevation<br/> Guest users restricted permissions<br/> Secure Access Workstation (SAW) for admins<br/> admin‑approved app consent<br/>apps must register in  authoritative CMDB<br/> two‑year log retention<br/> centralized certificate  lifecycle.
| **Additional  production environments** (auxiliary  tenants)<br/><br/> Production scenarios intentionally  isolated from core, when isolation reduces risk to primary environments or avoids constraints like product limitations. | Mergers and acquisitions (e.g. LinkedIn)<br/><br/>Use-case specific environments (e.g. PCI resources). | Long‑lived | Strict. Governed intake and triage. | Same security bar as core. |
| **Temporary  non-production environments** (ephemeral  tenants)<br/><br/>Short‑lived tenants for demos,  validation, troubleshooting. | Temporary environments for validating functionality.<br/><br/>Short‑term environments used for demonstrations or troubleshooting. | 90‑day maximum with extensions by deputy CISO. | No B2B or  multi‑tenant app paths to production environments.<br/>Strong MFA<br/>FIDO2/Auth App only<br/> Baseline  CA policies<br/> Entra ID P2 or E5 required for advanced security features. |
| **Unsanctioned  tenants** (satellite  tenants)<br/><br/> Legacy, non‑compliant, weak  attribution. Historically had unintended access paths. |  | Target state: decommission | Quarantined. Scream test and  accelerated retirement | Only temporary containment<br/>migrate/adopt ephemeral or converge into a few Auxiliary tenants where justified. |

## Guidance

Designing the right Microsoft Entra tenant architecture is a strategic decision that balances security, compliance, administrative complexity, and user experience. 

While a single production tenant is recommended for simplicity and user experience optimization, some organizations (including Microsoft) face business and technical requirements that drive the adoption of
multiple tenants.
 
Organizations must minimize the number of tenants while meeting isolation and regulatory needs, using multiple tenants only where they add clear, intentional value to reduce risk.

| **Use case** | **Recommended action** | **Resource** |
| --- | --- | --- |
| **Discover and classify** | - Restrict create tenant permissions in sanctioned/managed  tenants with Microsoft Entra.<br/>- Discover your Microsoft cloud footprint and build a full  inventory across Microsoft cloud footprint using billing/subscription  telemetry, M365 sign‑in/audit logs, and app consent data. - <br/>Define your own tenant classification nomenclature based on  your requirements. <br/>- Classify tenants per your organizations criteria and  attribute clear ownership. | [Default  user permissions](/entra/fundamentals/users-default-permissions)<br/><br/>[Discover  your Microsoft cloud footprint](/azure/cost-management-billing/manage/discover-cloud-footprint). |
| **Quarantine and regain control** | - Quarantine unknown/legacy tenants with tenant restrictions  and block-by-default inbound trust using cross-tenant access settings.<br/> - Use time‑bound **scream tests** to validate business  dependency and reduce false positives.<br/> - Where you own the tenant but lack admin rights, open a support process to regain access and bring to baseline. | [Cross-tenant  access overview](/entra/external-id/cross-tenant-access-overview)<br/><br/>[Configure tenant restrictions](/entra/external-id/tenant-restrictions-v2) |
| **Enforce lifecycle and baselines** | - Enforce classification criteria and security controls through  controlled tenant creation workflows. These workflows should include  mechanisms to attribute ownership to individuals in the organization.<br/>- Actively retire environments that dont meet standards. |  |
| **Modernize platforms and secrets** | - Migrate off legacy stacks (e.g., ASM → ARM)<br/>Eliminate shared secrets.<br/>Prioritize managed identities<br/>Store secrets in Azure Key Vault. | [Architecture  strategies for protecting application secrets](/azure/well-architected/security/application-secrets)<br/><br/>[Managed  identity best practice recommendations](https://learn.microsoft.com/entra/identity/managed-identities-azure-resources/managed-identity-best-practice-recommendations) |

![](images/Update-Pnp-Article-TenantSegmentation-Feb2026/image002-2.png)

## Outcomes

### Benefits

- **Reduced attack surface:** Eliminates outdated/misconfigured tenants and removes
 unintended traversal paths
- **Containment of compromise:** Strong isolation and policy enforcement limit lateral movement
- **Improved governance:** Lifecycle and intake policies drive a secure-by-default
 approach
- **Operational efficiency:** Less technical debt, clearer ownership, and simpler access
 models

### Trade‑offs

- Cross‑business coordination to
 classify, migrate, and retire tenants
- Investment in automation for discovery,
 classification, and expiration
- Temporary disruption for low‑value
 test environments during cleanup
- Cultural change to adopt tenant lifecycle
 patterns (including time-bound if applicable) and to standardize exception
 handling

# Key success factors

Track and review, at least quarterly:

- Number of unused or unmanaged tenants identified and removed.
- Percentage of tenant environments classified and governed under standardized policies, with up-to-date
 ownership information.
- Migration rate from legacy infrastructure (e.g., ASM to ARM).
- Reduction in authentication activity from legacy systems or high-risk tenants.
- Enforcement rate of Conditional Access policies and additional security controls across all tenant types.

![](images/Update-Pnp-Article-TenantSegmentation-Feb2026/image002-3.png)

# Summary

Organizations that systematically **discover, segment, and eliminate** legacy systems and unmanaged tenants dramatically improve their security posture. By shrinking the attack surface, enforcing tenant lifecycle governance, and aligning with Zero Trust architecture, enterprises build resilience against modern threatswithout sacrificing agility where short‑lived tenants are appropriate. 

By removing legacy systems that risk security, you can improve your organizations security posture by reducing
attack surfaces and eliminating legacy vulnerabilities.
