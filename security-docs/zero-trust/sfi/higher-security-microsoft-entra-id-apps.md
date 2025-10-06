---
title: Higher security for Entra ID apps
description: Higher security for Entra ID apps is part of the protect tenants and isolate production systems pillar of the Secure Future Initiative (SFI). This pillar focuses on minimizing the potential impact of security incidents through eliminating legacy and unmanaged tenants, implementing consistent security practices, and enforcing continuous least-privilege access.
ms.date: 10/03/2025
ms.service: security
author: leonyen
ms.author: v-leonyen
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Higher security for Entra ID apps (Secure Future Initiative)

**Pillar name: Protect tenants and isolate production systems**<br />
**Pattern name: Higher security for Entra ID apps**

## Context and problem

Microsoft Entra ID provides a single identity system for cloud and on-premises apps within an organization. As identity systems become more interconnected and integral to application access, they also become a prime target for attackers.  

Microsoft Entra ID applications, if improperly secured, can:

- Enable lateral movement via cross-tenant pivot points  
- Be exploited through weak authentication or excessive permissions  
- Store secrets insecurely or permit outdated legacy protocols  
- Become shadow infrastructure if their lifecycle is not governed  

A breach in even a non-production or lightly used application can grant access to sensitive environments, especially when multi-tenant configurations or guest users are involved. Recent high-profile attacks have shown that attackers often compromise identity systems through overlooked applications or external service principals. The challenge is ensuring every app—regardless of its tenant or usage level—is governed to a consistent, high security standard.  

## Solution

Microsoft implemented the **Higher security for Entra ID apps** objective under the Secure Future Initiative (SFI) to raise the security bar for all applications using Microsoft Entra ID. The goal: manage 100% of apps to a secure, consistent baseline through automation, hardening, and lifecycle governance.

**Key measures taken include:**

- Removal of 730,000 unused applications across productivity and production environments.  
- Deployment of Entra application layering policies to restrict multi-tenant app behavior.  
- Mandating global admin consent for any external organization requesting app access.  
- Application certificate and secret restrictions, including enforcement of Azure Key Vault locality and PKI origin.  
- Blocking guest user access to all apps not explicitly reviewed and approved.  
- Application-specific Conditional Access enforcement, with policies that restrict external authentication and enforce least privilege.  

Together, these actions reduced Microsoft's app-level attack surface, removed unmanaged service principals, and locked down external access—without compromising operational flexibility.  

## Guidance
Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| App registration security | <ul><li>Restrict who can register applications in Entra ID and enforce review processes for new app registrations.</li><li>Applications should have explicit assignment or scoped provisioning.</li></ul>| [Delegate application management administrator permissions – Microsoft Entra ID](/entra/identity/role-based-access-control/delegate-app-roles#restrict-who-can-create-applications) |
| Phishing-resistant passwordless authentication | Enforce continuous least-privilege access using phishing-resistant authentication methods. | [Get started with a phishing-resistant passwordless authentication deployment in Microsoft Entra ID](/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication) |
| Certificate and secret management | <ul><li>Use Privileged Identity Management (PIM) for just-in-time (JIT) and just-enough-access (JEA) to minimize standing admin privileges.</li><li>Replace long-lived client secrets with certificates or managed identities to reduce credential risk.</li></ul> | [Migrate applications away from secret-based authentication – Microsoft Entra ID](/entra/identity/enterprise-apps/migrate-applications-from-secrets) |
| Consent and permissions governance | Limit user and admin consent to only approved applications and monitor requested API permissions | [Configure the admin consent workflow – Microsoft Entra ID](/entra/identity/enterprise-apps/configure-admin-consent-workflow) |
| Conditional Access for apps | Apply Conditional Access policies to applications, requiring compliant devices, strong authentication, or specific network conditions. | [Conditional Access policy templates: Simplify security – Microsoft Entra ID](/entra/identity/conditional-access/concept-conditional-access-policy-common) |


## Benefits 
- **Reduced lateral movement risk:** Pivot points between tenants are eliminated or restricted.  
- **Consistent app hardening:** All applications meet a known, enforced security standard.  
- **Lifecycle control:** Shadow or legacy apps are removed or remediated.  
- **Credential security:** Secrets are replaced with managed identities and key vault governance.  
- **External user control:** Guest access is monitored, limited, and revocable through review workflows.  


## Trade-offs 
- Deep discovery and classification of existing Entra apps across multiple environments.  
- Automation of lifecycle controls, including expiration, consent management, and soft deletion.  
- Reduction in user autonomy around app consent, replaced with administrative workflows.  
- Changes to service principal management, certificate issuance, and default authentication behaviors.  

## Key success factors

- Percentage of apps governed by security baselines and Conditional Access policies  
- Number of abandoned or outdated apps removed quarterly  
- Credential reuse or over-permissioned app metrics  
- Guest user access reductions tied to access reviews 

## Summary

Entra ID applications can become a strategic security advantage. By applying practices such as lifecycle governance and credential control, apps that were previously potential risk points can become trusted, hardened access pathways that are essential to your Zero Trust architecture.  

**Further harden your Entra ID apps today and better secure every identity, app, and access point across your tenant ecosystem.**  
