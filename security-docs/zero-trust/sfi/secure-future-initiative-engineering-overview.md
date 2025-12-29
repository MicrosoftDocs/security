---
title: Protect engineering systems in the Microsoft Secure Future Initiative (SFI)
description: Learn how to protect engineering systems in Microsoft's Secure Future Initiative (SFI).
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

# Protect identities and secrets in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of engineering pillars by means of processes, standards, and continuous improvements.

This article summarizes the "Protect identities and secrets" SFI pillar.

## Before you start

- [Review](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars
- [Review tthe latest progress on pillar objectives](secure-future-initiative-whats-new.md#pillar-progress) in What's New.


## Pillar and objectives 

The aim of the "Protect identities and secrets" pillar aims to strengthen trust in every identity and credential used across Microsoft systems by eliminating weaknesses in how accounts, tokens, and secrets are issued, stored, and used. It reduces the risk of unauthorized access by enforcing standards to harden the identity and secrets infrastructure, and to control user and application authentication and authorization. 

Microsoft objectives for this pillar are summarized in the following table. You can see how each objective maps toZero Trust principles, and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).

**Pillar objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Protect cryptographic signing keys**<br/><br/>Protect identity infrastructure signing and platform keys with rapid and automatic rotation of identity infrastructure keys, using hardware storage and protection. | **Verify explicitly**: Protect identity signing assets. Strong attestation of keys built into workflow.<br/><br/>**Assume breach**: Protect keys as if compromise can occur, using hardware‑assisted isolation. | **PR.AA-04**: Keys are only accessible to verified identities.<br/><br/>**PR.PS-01**: Protect cryptographic assets on hardware/software platforms.
**2. Adopt standard SDKs for identity**<br/><br/>Strengthen identity standards and drive standards adoption with the use of standard SDKs across applications, so that apps and services use a uniform, hardened library for validating tokens. |  **Verify explicitly**: Standard validated libraries reduce variability and risk. Use consistent validation.<br/><br/>**Assume breach**: Reduces attack surface from custom implementations. | **PR.AA-01**: Define rules for SDK access.<br/><br/>**PR.AA-02**: Manage accounts used in SDK validation.<br/><br/>**PR.AA-03**: Enforce token validation through standardized SDK.
**3. Enforce phishing-resistant MFA**<br/><br/>Ensure user accounts are protected with securely manEnforcaged, phishing-resistant MFA.  | **Verify explicitly**: Strong authentication techniques verify user identity every access attempt.<br/><br/>**Use least privilege**: MFA strengthens least‑privilege enforcement by reducing unauthorized access. | **PR.AA-01**: Policies require MFA.<br/><br/>**PR.AA-03**: MFA enforced on all accounts.
**4. Safe secrets standard**<br/><br/> Shift away from long-lived secrets such as service account credentials to ensure that applications are protected with system-managed credentials such as managed identities. | **Use least privilege**: Restrict secret access. Avoid hard‑coded or persistent credentials.<br/><br/>**Assume breach**: Treat every secret as potentially compromised unless strongly guarded. | **PR.AA-04**: Only verified identities can access secrets.<br/><br/>**PR.DS-01**: Secrets are encrypted and protected.<br/><br/>**PR.PS-01**: Secret management systems implemented are secure platforms to protect sensitive data.
**5. Stateful validation for identity tokens**<br/><br/>Ensure identity tokens are protected with stateful and duration validation. | **Verify explicitly**: Fully validate identity tokens at every enforcement point.<br/><br/>**Assume breach**: Ensure invalid or malformed tokens are rejected. | **PR.AA-03**: Token validation enforced in access decisions.<br/><br/>**DE.AE-02**: Anomalous activity detection. Detect unusual token usage.<br/><br/> **DE-AE-03**: Uauthorized activity detection. Monitor for misuse or compromised tokens.
**6. Fine-grained key partitioning**<br/><br/>Adopt more fine-grained partioning of identity signing keys and platform keys. | **Use least privilege**: Partitioning limits privilege scopes for key usage.<br/><br/>**Assume breach**: Limits impact if key segment is compromised. | **PR.AA-04**: Identity proofing. Verify identities accessing each key partition.<br/><br/>**PR.AA-05**: Separation of duties. Isolate key operations to enforce limited privileges.
**7. Quantum-safe PKI systems**<br/><br/>Ensure identity and certificate PKI systems are ready for a post-quantum cryptography world. | **Verify explicitly**: Use post‑quantum cryptography for identity assertions.<br/><br/>**Assume breach**: Anticipate future threats; prepare for stronger resistance. | **PR.AA-04**: Identity proofing. Only authorized identities management PKI operations.


## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.