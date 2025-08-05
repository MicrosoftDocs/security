---
title: Remove legacy systems that risk security – Zero Trust
description: Remove legacy systems that risk security is part of the protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI), focusing on removing legacy and unmanaged tenants to reduce Microsoft’s attack surface.
ms.date: 08/05/2025
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Remove legacy systems that risk security (Secure Future Initiative)

**Pillar name: Protect tenants and isolate production systems**<br>
**Pattern name: Remove legacy systems that risk security**

## Context and problem

Modern threat actors exploit unmanaged, legacy, or employee-created tenants that lack modern security controls. These tenants often:

- Operate outside centralized governance

- Lack MFA, Conditional Access, and compliance enforcement

- Introduce configuration drift and lateral movement paths

- Persist long after their intended use (e.g., test/demo environments)

In production environments, these risks are amplified. A single compromised legacy tenant can serve as a launchpad for broader attacks, undermining Zero Trust principles and exposing sensitive systems.

## Solution

Microsoft implemented a comprehensive cleanup initiative under the Secure Future Initiative (SFI) to eliminate legacy and unmanaged tenants. Key actions included:

- Discovery and cleanup of 6 million Entra ID tenants, removing 5.75 million that were abandoned or insecure.

- Automated tenant lifecycle policies, including a 90-day expiration for ephemeral tenants.

- Migration from legacy infrastructure, such as Azure Service Management (ASM) to updated infrastructure with Azure Resource Manager (ARM), reaching 88% completion.

- Tenant segmentation and hardening, using Conditional Access, logical layering, and pre-configured security baselines.

- Policy-driven tenant creation, requiring approval and enforcement of “secure by default” principals.

This approach significantly reduced Microsoft’s attack surface and improved governance across its identity infrastructure.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Inventory and classification   | <ul><li>Identify and retire unused tenants</li><li>Classify tenants as production, auxiliary, or ephemeral</li><li>Monitor tenant creation via Entra ID logs</li>  | [Discover your Microsoft cloud footprint FAQ](/azure/cost-management-billing/manage/discover-cloud-footprint)  |
| Modernization   | <ul><li>Migrate from Azure Service Manager (ASM) to Azure Resource Manager (ARM)</li><li>Audit access, device compliance, and authentication methods</li><li>Harden legacy applications with secure defaults</li></ul> | [What is Azure Resource Manager?](/azure/azure-resource-manager/management/overview)  |
| Lifecycle enforcement   | <ul><li>Implement expiration policies (e.g., 90-day for non-production)</li><li>Require VP or IT approval for tenant creation</li><li>Auto-deauthorize expired tenants</li></ul> | <ul><li><a href="/entra/identity/conditional-access/managed-policies">Microsoft-managed Conditional Access policies</a></li><li><a href="/microsoft-365/solutions/tenant-management-overview">Tenant management for Microsoft 365 for enterprise </a></li></ul> |
| Access control | <ul><li>Enforce Conditional Access across all tenants</li><li>Define per-environment access rules</li><li>Use graph-based tools to detect attack paths</li></ul> | [Conditional Access policy templates](/entra/identity/conditional-access/concept-conditional-access-policy-common)  |
| Secrets hygiene | <ul><li>Eliminate shared secrets</li><li>Use Managed Identities</li><li>Store secrets in Azure Key Vault</li></ul> | [About Azure Key Vault](/azure/key-vault/general/overview)  |

## Outcomes

### Benefits

- Reduced attack surface: Outdated, misconfigured, or abandoned systems no longer expose the environment.

- Minimized the ability for lateral movement: Logical isolation and policy enforcement contain potential intrusions.

- Improved governance: Tenant lifecycle policies ensure environments are secure by default.

- Lower operational complexity: Removal of technical debt streamlines management and oversight.

### Trade-offs

- Significant coordination across business units and engineering teams

- Creation of automated systems for tenant discovery, classification, and expiration

- Development of clear tenant classification standards (e.g., production, auxiliary, ephemeral)

- Temporary service disruption for some non-critical test environments during cleanup

- Investment in new policies, monitoring tools, and enforcement mechanisms to prevent future debt

## Key success factors

To track success, measure the following:

- Number of unused or unmanaged tenants identified and removed

- Percentage of tenant environments classified and governed under standardized policies

- Migration rate from legacy infrastructure (e.g., ASM to ARM)

- Reduction in authentication activity from legacy systems or high-risk tenants

- Enforcement rate of Conditional Access policies across all tenant types

## Summary

Organizations that systematically eliminate legacy systems and unmanaged tenants dramatically improve their security posture. By shrinking the attack surface, enforcing tenant lifecycle governance, and aligning with Zero Trust architecture, enterprises can build more resilient environments and ensure their infrastructure is prepared to defend against modern threats.

**By removing legacy systems that risk security, you can improve your organization’s security posture by reducing attack surfaces and eliminating legacy vulnerabilities.**
