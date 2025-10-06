---
title: Zero Trust for source code access (Secure Future Initiative) – Zero Trust 
description: Secure all tenants and their resources is part of the Protect engineering systems pillar of the Secure Future Initiative (SFI), which focuses on reducing attack surface and lateral movement risk by enforcing strict tenant governance, modernizing platform dependencies, and isolating production access. It emphasizes Zero Trust by default, ensuring that every tenant, system, and user operates under minimum necessary access and hardened boundaries. 
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

# Zero Trust for source code access (Secure Future Initiative)

**Pillar name: Protect engineering systems**<br />
**Pattern name: Zero Trust for source code access**

Microsoft adopted a Zero Trust approach to protect its source code, requiring identity-verified checks for all code changes. Key measures include multifactor authentication for pull requests and strict protections for production branches, reducing the risk of unauthorized merges.

## Context and problem
Source code is one of the most valuable assets in any organization. At Microsoft, tens of thousands of repositories and millions of lines of code underpin the services and products used by billions worldwide. This makes source code a high-value target for adversaries, who can exploit unauthorized access to inject malicious changes, steal intellectual property, or undermine customer trust.

Historically, protections such as repository permissions and branch policies provided a baseline of control. However, as attackers grow more sophisticated—leveraging stolen credentials, automation, and supply chain vectors—traditional access controls are no longer sufficient. Incidents across the industry show how a single compromised account or unchecked pull request can have a downstream impact on millions of users. 

To address this, Microsoft operationalized a Zero Trust approach to source code access to help ensure that no code reaches production without rigorous, identity-verified, and auditable checks.

## Solution

Microsoft's approach applies Zero Trust principles directly to engineering systems. This means access to source code and the ability to merge changes into production branches require continuous verification, least privilege enforcement, and strong proof of presence.

**Key elements include:**

- **Proof of Presence for Pull Requests (PoP PR):** Introduced in 2024 and rolled out across 61,000 repositories, PoP PR ensures every pull request to a protected branch is authenticated by a real, verified individual using fresh multifactor authentication (MFA).  
- **Tiered authentication methods:** Depending on project sensitivity, engineers use software authenticators (Windows Hello, Face ID), hardware tokens (FIDO2 YubiKeys), or production identities tied to Secure Access Workstations (SAWs).  
- **Branch classification and enforcement:** Production branches (`main`, `master`, `default`) are automatically tagged and protected, ensuring uniform enforcement across the enterprise.  
- **Exception governance:** Limited, reviewed, and auditable exemptions (e.g., for automation) are tracked in a software asset management system with executive sign-off.  

By embedding Zero Trust checks into the software development lifecycle, Microsoft prevents unauthorized code merges, reduces the risk of privilege escalation, and strengthens accountability.
  

## Guidance
Organizations can adopt a similar pattern using the following actionable practices:

| **Use case** | **Recommended action** | **Resource** |
|---------------|------------------------|----------------|
| **Conditional access** | - Create a Conditional Access policy to require users who access the Azure Service Management API suite to use multifactor authentication (MFA). | [Require MFA for Azure management with Conditional Access](/entra/identity/conditional-access/policy-old-require-mfa-azure-mgmt) |
| **Authentication strength** | - Use FIDO2 hardware tokens or Secure Access Workstation (SAW)-bound identities for high-sensitivity repositories. | [Plan a phishing-resistant passwordless authentication deployment in Microsoft Entra ID](/entra/identity/authentication/how-to-deploy-phishing-resistant-passwordless-authentication) |
| **Automation exceptions** | - Limit exemptions to cases where human review is infeasible; track approvals in a governance system. | [Reviewing the audit log for your organization – GitHub Docs](https://docs.github.com/en/organizations/keeping-your-organization-secure/managing-security-settings-for-your-organization/reviewing-the-audit-log-for-your-organization) |
| **Code review rigor** | - Require at least two reviewers and enforce successful build policies before merging. | [Git branch policies and settings – Azure DevOps](/azure/devops/repos/git/branch-policies) |
| **Secure-by-default pipelines** | - Integrate GitHub Advanced Security for secret scanning, dependency management, and code scanning. | [About GitHub Advanced Security](https://docs.github.com/en/get-started/learning-about-github/about-github-advanced-security) |


## Benefits 
- **Stronger supply chain resilience:** Prevents unauthorized or automated changes to production code.  
- **Improved accountability:** Every change is traceable to a verified individual with auditable logs.  
- **Scalable protection:** Integration into a standardized, shared set of tools and rules that provide protections for over 100,000 engineers with minimal disruption.  

## Trade-offs 
- **Developer friction:** Fresh MFA at merge points can add time and perceived inconvenience.  
- **Infrastructure investment:** Requires hardware tokens, Secure Access Workstations (SAWs), and integration with engineering platforms.  
- **Exemption management:** Governance for automated scenarios demands ongoing oversight.  
- **Adoption curve:** Teams must adjust workflows to align with stricter enforcement and branching policies.  

## Key success factors

To track success, measure the following:

- **Percentage of production repositories** protected by Proof of Presence (PoP) policies.  
- **Daily number of authenticated pull requests** completed without policy bypass.  
- **Reduction in unauthorized or anomalous code merge attempts.**  
- **Compliance with internal audit requirements** for exception management.  
- **Engineer satisfaction and adoption metrics** balanced with security enforcement.  

## Summary

Zero Trust for source code access helps to ensure that Microsoft's most critical intellectual property—its source code—is better protected against insider threats, compromised credentials, and automated attacks. By requiring proof of presence, enforcing branch classification, and scaling Zero Trust protections, Microsoft has strengthened its entire software supply chain.

With the right practices, organizations can apply the same approach: enforce strong identity checks at every code merge, adopt MFA and hardware-backed authentication, and maintain auditable governance. These measures create a resilient engineering system that upholds developer productivity and security.

**Adopt Zero Trust for source code access today and safeguard the integrity of your software development lifecycle.**
