---
title: Protect identities and secrets in the Microsoft Secure Future Initiative (SFI)
description: Learn how to protect identities and secrets in Microsoft's Secure Future Initiative (SFI).
ms.date: 11/03/2025
ms.service: security
author: rayne-wiselman
ms.author: raynew
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Overview - Protect identities and secrets

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. SFI is built upon:

- A set of security principles that drive the way in which we innovate on security design, implement those innovations into Microsoft products as secure defaults and standards, and provide internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).

This article provides an overview of the "Protect identities and secrets" SFI pillar. 

## Before you start

- [Learn about](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars.
- [Review and track the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in the SFI What's New article.
- Pillar objectives map to [Zero Trust principles](zero-trust/zero-trust-overview), and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms](secure-future-initiative-overview.md#nist-functions) to help as you review the table.

## Pillar and objectives 

The "Protect identities and secrets" pillar aims to:

- Strengthen trust in every identity and credential used across Microsoft systems by eliminating weaknesses in how accounts, tokens, and secrets are issued, stored, and used.
- Reduce the risk of unauthorized access by enforcing standards to harden the identity and secrets infrastructure, and to control user and application authentication and authorization.

Microsoft objectives and Zero Trust/NIST mapping for this pillar are summarized in the following table.

**Pillar objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | **Verify explicitly**: Protect identity signing assets. Build strong attestation of keys into workflows.<br/><br/>**Assume breach**: Protect keys as if compromise can occur, using hardware‑assisted isolation. | **PR.AA-04**-Access is restricted using segmentation and least privilege.<br/>Protection of cryptographic keys relies on strict access segmentation and least-privilege authorization to restrict key used to isolated, dedicated key vault environments, and removing unneeded access and lateral movement paths to key storage.<br/><br/>**PR.PS-01**: Assets are formally evaluated to ensure they meet security requirements before being approved for use.<br/>Keys must be generated and stored in accordance with secure-by-default standards.
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. |  **Verify explicitly**: Standard validated libraries reduce variability and risk. Use consistent validation.<br/><br/>**Assume breach**: Reduces attack surface from custom implementations. | **PR.AA-01**: Identities are authenticated commensurate with risk.<br/>Using standard SDKs enforces strong, consistent authentication flows.<br/><br/>**PR.AA-02**-Access is authorized using role‑based attributes.<br/>Standard SDKs integrate with Microsoft Entra RBAC and enforce role-aware token claims.<br/><br/>**PR.AA-03**: Access is authorized using attribute‑based/contextual attributes.<br/>Standard SKDs automatically apply conditional access, ddevice context, MFA requirements, and risk signal for contextual authorization.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely manEnforcaged, phishing-resistant MFA.  | **Verify explicitly**: Strong authentication techniques verify user identity every access attempt.<br/><br/>**Use least privilege**: MFA strengthens least‑privilege enforcement by reducing unauthorized access. | **PR.AA-01**: Identities are authenticated commensurate with risk.<br/>Phishing-reisistant MFA uses strong, risk-appropriate authentication.<br/><br/>**PR.AA-03**: Access is authorized using attribute‑based and contextual attributes.<br/>Phishing-resistant MFA strengthens contextual-access decisions.
**4. Safe secrets standard**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | **Use least privilege**: Restrict secrets access. Avoid hard‑coded or persistent credentials.<br/><br/>**Assume breach**: Treat every secret as potentially compromised unless strongly guarded. | **PR.AA-04**: Access is restricted using segmentation and least‑privilege principle.<br/>Safe secrets standards restrict which identity and services can access or use secrets, enforcing least-privilege and eliminating lateral movement paths caused by static credentials.<br/><br/>**PR.DS-01**: Data is managed consistent with enterprise requirements.<br/>Secrets are handling in accordance with lifecycle and storage requirements, such as centralized vaulting, rotation, and logging.<br/><br/>**PR.PS-01**: Assets are formally evaluated to ensure they meet security requirements before being approved for use.<br/>Using safe secrets means that apps and services must comply with security baselines.
**5. Stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation. | **Verify explicitly**: Fully validate identity tokens at every enforcement point.<br/><br/>**Assume breach**: Ensure invalid or malformed tokens are rejected. | **PR.AA-03**: Access is authorized using attribute‑based and contextual attributes.<br/>Token validation supplies real-time identity context for authorization decisions.<br/><br/>**DE.AE-02**: Detected events are analyzed to understand attack targets and methods.<br/>Stateful validation detects anomalous activity such as forged tokens, and unusual token usage.<br/><br/> **DE.AE-07**: Processes detect and analyze anomalous activity to support response and recovery.<br/>Since tokens are checked continuously, SFI can identity and respond quicky to unauthorized token activity to improve detection and shrink attacker dwell times.
**6. Fine-grained key partitioning**<br/><br/>Adopt more fine-grained partioning of identity signing keys and platform keys. | **Use least privilege**: Partitioning limits privilege scopes for key usage.<br/><br/>**Assume breach**: Limits impact if key segment is compromised. | **PR.AA-04**: Access is restricted using segmentation and least‑privilege principles.<br/>Fine-grained key partitioning enforces strict segmentation of key material, preventing lateral movement across key assets.<br/><br/>**PR.AA-05**: Permissions and authorizations are managed, enforced, and periodically verified.<br/>Partitioned keys require tight authorization controls, continuous verification, and boundary enforcment to ensure that only correct services identities can access isolated key partitions.
**7. Quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | **Verify explicitly**: Use post‑quantum cryptography for identity assertions.<br/><br/>**Assume breach**: Anticipate future threats; prepare for stronger resistance. | **PR.AA-04**: Access is restricted using segmentation and least‑privilege principles.<br/>Quantum-safe PKI requires segmented, least-privilege access to key-signing systems, CAs, HSMS etc.


## Next steps

- [Review the latest progress on pillar objectives](secure-future-initiative-whats-new.md#pillar-progress) in What's New.
- [Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.