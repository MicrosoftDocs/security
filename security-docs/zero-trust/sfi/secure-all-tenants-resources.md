---
title: Secure all tenants and their resources - Microsoft Secure Future Initiative
description: Secure all tenants and their resources is a part of the Protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI). This pillar focuses on minimizing the potential impact of security incidents through strong tenant isolation, segmentation, and attack surface reduction. 
ms.date: 10/03/2025
ms.service: security
ms.subservice: zero-trust
ms.topic: concept-article
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Secure all tenants and their resources (Secure Future Initiative)

**Pillar name: Protect tenants and isolate production systems**<br />
**Pattern name: Secure all tenants and their resources**

To reduce the security risks of untracked tenants and lack of visbility, Microsoft has implemented the Secure all tenants and their resources pattern. This ensures comprehensive governance and security across all tenants, aligning with Zero Trust principles.

## Context and problem

The first step in tenant security is discovery. Without a complete inventory, security and governance cannot succeed. Many organizations lack visibility into active, legacy, and shadow tenants, leaving untracked environments vulnerable to exploitation.

Microsoft has invested heavily in identifying and cataloging all tenants across its environments. This includes production, productivity/test, and ephemeral tenants. Without robust discovery and lifecycle governance, even seemingly low-risk tenants can become shadow infrastructure—unmonitored, unpatched, and exploitable as pivot points for attackers.

**Key risks include:**
* Lateral movement from non-production into production tenants.
* Stale or inactive tenants with no security baselines or lifecycle controls.
* Shared secrets and misconfigurations enabling credential reuse across tenants.

## Solution

As part of the Secure Future Initiative (SFI), Microsoft implemented the secure all tenants and their resources objective by enforcing tenant baselines, governing lifecycle management, and standardizing protections across its cloud environments.

* **Standardized security logging library**: Ensures consistent data capture across services, reducing observability gaps.
* **Centralized log collection**: Specialized investigator accounts provide unified access to cross-service logs, simplifying correlation and speeding up investigations.
* **Extended log retention**: Audit logs retained for up to two years across Microsoft services, to enable forensic investigation of long-term attack patterns.
* **Advanced detection analytics**: Integration of machine learning and AI-powered models improves detection of complex attack techniques and reduces false positives.
* **Expanded customer logging**: Microsoft increased standard audit log retention for Microsoft 365 customers to 180 days, with options for longer retention.

Microsoft's approach includes:
* **Security baselines**: Preconfigured tenant security templates to ensure consistency and accelerate hardening.
* **Tenant classification and lifecycle governance**: Categorizing tenants by purpose (production, productivity, auxiliary, ephemeral) and applying default controls accordingly. 
* **Conditional Access enforcement**: Governing authentication and authorization at scale, including ephemeral tenants and unmanaged accounts.
* **Secure Admin Workstations (SAWs)**: Hardware-isolated devices separating privileged from productivity access.
* **Monitoring and analytics:** Centralized security data via audit logs, Microsoft Secure Score, and Defender integration.
* **Secret management and credential isolation**: Preventing shared secrets between tenants and enforcing phishing-resistant MFA.
* **Lateral movement prevention:** Prevented lateral movement by isolating production vs. non-production tenants.
* **Legacy and inactive tenants:** Decommissioned legacy and inactive tenants via lifecycle audits.
* **Posture visibility:** Improved posture visibility with Secure Score across the tenant fleet.
* **Tenant sprawl:** Reduced tenant sprawl and enforced strict controls on new tenant creation.

These steps ensure all tenants—regardless of purpose or origin—are visible, governed, and protected in line with Zero Trust principles.

## Guidance
Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Baseline security controls   | Apply Microsoft security defaults across all tenants, then extend with Microsoft 365 Lighthouse baselines for enterprise-scale hardening.| <ul><li>[Configure Security Defaults for Microsoft Entra ID](/entra/fundamentals/security-defaults)</li><li>[Overview of using Microsoft 365 Lighthouse baselines to deploy standard tenant configurations](/microsoft-365/lighthouse/m365-lighthouse-deploy-standard-tenant-configurations-overview)</li><li>[Architecture strategies for establishing a security baseline](/azure/well-architected/security/establish-baseline)</li></ul> |
| Conditional Access |<ul><li>Deploy baseline Conditional Access (CA) policies: block legacy authentication, require MFA for all users, and enforce device compliance for privileged roles.</li><li>Expand with risk-based and location-aware policies.</li></ul> | <ul><li>[Conditional Access policy templates – Microsoft Entra ID](/entra/identity/conditional-access/concept-conditional-access-policy-common?tabs=secure-foundation)</li><li>[Plan your Microsoft Entra Conditional Access deployment](/entra/identity/conditional-access/plan-conditional-access)<br>[Best practices to secure with Microsoft Entra ID](/entra/architecture/secure-best-practices)</li></ul> |
| Privileged access management | Use Privileged Identity Management (PIM) for just-in-time (JIT) and just-enough-access (JEA) to minimize standing admin privileges. | <ul><li>[Plan a Privileged Identity Management deployment](/entra/id-governance/privileged-identity-management/pim-deployment-plan)</li><li>[Activate Microsoft Entra roles in PIM – Microsoft Entra ID Governance](/entra/id-governance/privileged-identity-management/pim-how-to-activate-role)</li></ul> |
| Tenant isolation |<ul><li>Separate production and non-production tenants.</li><li>Eliminate shared admin accounts and app registrations across environments.</li><li>Apply distinct Conditional Access baselines per tenant type.</li></ul>| <ul><li>[Resource isolation with multiple tenants to secure with Microsoft Entra ID](/entra/architecture/secure-multiple-tenants)</li><li>[Restrict cross-tenant inbound and outbound access – Power Platform](/power-platform/admin/cross-tenant-restrictions?tabs=new)</li></ul> |
| Monitoring and threat detection |<ul><li>Combine Microsoft Defender for Identity (on-premises AD signals) with Microsoft Entra ID Protection (cloud-based risk signals).</li><li>Centralize monitoring to detect lateral movement, token theft, and abnormal sign-in behavior.</li></ul> | <ul><li>[Microsoft Defender for Identity deployment overview](/defender-for-identity/deploy/deploy-defender-identity)</li><li>[What is Microsoft Entra ID Protection?](/entra/id-protection/overview-identity-protection)</li><li>[What are risk detections? – Microsoft Entra ID Protection](/entra/id-protection/concept-identity-protection-risks)</li></ul> |


## Benefits 
* **Standardized hardening:** Security baselines ensure all tenants meet minimum protection thresholds.  
* **Reduced attack surface:** Legacy, shadow, and unused tenants are systematically retired.  
* **Improved governance:** Central inventory and classification support continuous compliance and oversight.  
* **Controlled access:** Conditional Access, role-based access control (RBAC), and multifactor authentication (MFA) protect identities and limit external sharing risks.  
* **Enhanced detection and response:** Integrated security data and logs provide visibility across all tenants. 

## Trade-offs 
Implementing this approach requires:

* Establishing centralized ownership of tenant lifecycle policies. 
* Investment in automation (default policy application, expiration workflows).
* Possible re-architecture of access models (e.g., separating prod/non-prod). SAW adoption introduces initial device complexity and cost.
* Training and enforcement needed to eliminate shadow tenants and credential reuse.

## Key success factors
To track success, measure the following:
* Percentage of tenants with enforced security baselines
* Number of legacy or shadow tenants decommissioned
* Coverage of centralized inventory and compliance reporting
* Percentage of identities with MFA enabled
* Secure Score improvement across Microsoft Secure Score metrics
* Volume of blocked legacy authentication attempts or unauthorized sharing events

## Summary
Securing all tenants and their resources is foundational to Microsoft's SFI pillars: **Secure by Design, Secure by Default, and
Secure Operations.**

With baseline policies, lifecycle governance, and continuous oversight, organizations can reduce risk, enforce consistent protections, and prevent shadow infrastructure from undermining security. At scale, this ensures every identity, access point, and tenant is secured by design.
