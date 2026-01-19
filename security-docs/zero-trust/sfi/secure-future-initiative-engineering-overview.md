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

# Overview - Protect engineering systems in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of focused engineering pillars by means of processes, standards, and continuous improvements.

This article summarizes the "Protect engineering systems" SFI pillar.

## Before you start

- [Learn about](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars.
- [Review and track the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in the SFI What's New article.
- Learn about [Zero Trust principles](../zero-trust-overview.md), and [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms](secure-future-initiative-overview.md#nist-functions) to help as you review the table in this article.

## Pillar and objectives 

The "Protect engineering systems" pillar aims to strengthen security across development and engineering by operationationalizing the asset inventory, implementing Zero Trust principles, securing pipelines, and strengthening isolation and resiliency.

Microsoft objectives and Zero Trust/NIST mapping for this pillar are summarized in the following table.

**Pillar objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Complete software asset inventory**<br/><br/>Inventory spans all Azure DevOps repositions and pipelines with full metadata. StartRight tooling ensures that 80% of assets are inventoried at creation, and rest are captured within 24 hours. This enables rapid incident response and universal policy enforcements. We increased inventory scope with more fine-grained ownership for better response. | **Verify explicitly**: Protect identity signing assets. Strong attestation of keys built into workflow. ><br/>**Assume breach**: Protect keys as if compromise can occur, using hardware‑assisted isolation. | **ID.AM-02** (*Software platforms and applications within the organization are inventoried*).<br/> Maintaining a complete inventory of all engineering software assets aligns directly with NIST’s requirement to track and govern all software/platform components.
**2. Zero Trust for source code access**<br/><br/>Reduced standing access for admin roles, and just-in-time elevation required. Azure DevOps OAuth-based apps leverage Microsoft Entra authentication with conditional access enforcement. Proof-of-presence checks cover almost all production code changes. |  **Verify explicitly**: Standard validated libraries reduce variability and risk. Use consistent validation.<br/><br/>**Assume breach**: Reduces attack surface from custom implementations. | **PR.AA-01** (*Identities are authenticated commensurate with risk*).<br/><br/>**PR.AA-02** (*Access is authorized using role‑based attributes*). <br/>Strong authentication before code access.<br/><br/>**PR.AA-03** (*Access is managed using contextual attributes*). <br/> Device, location, session risk checked before repo access.<br/><br/>**PR.AA-04** (*Access is restricted based on segmentation and least privilege*). <br/> Enforcement of repo, branch, and environment segmentation.<br/><br/>**PR.AA-05** (*Permissions are managed, enforced, and periodically verified*). <br/> Continuous review of code‑access permissions.<br/><br/>**PR.AA-06** (*Access aligns with least privilege*). <br/> Zero Trust assures minimal access to code repos.<br/><br/>**PR.DS-01** (*Data is managed consistent with enterprise policies*). <br/> Controls for handling sensitive source code.<br/><br/>**PR.DS-02** (*Data is protected when stored*). <br/> Repo encryption and secure storage for code.<br/><br/>**PR.DS-10** (*Access to data is monitored to detect unauthorized activity*). <br/> Monitoring source code for anomalies.
**3. Secure code development**<br/><br/>Code signing access is almost entirely locked to production identities. Repositories enforce branch policies with minimum approver counts. The scope of this objective has increased to optimize our secrets detection capabilities. We introduced analytics-driven validation to strengthen  compliance and durability, positioning us to reduce systemic risk  across  engineering workflows. | **Verify explicitly**: Strong authentication techniques verify user identity every access attempt.<br/><br/>**Use least privilege**: MFA strengthens least‑privilege enforcement by reducing unauthorized access. | **PR.AA-04** (*Access is restricted using segmentation and least privilege*). <br/> Pipeline design enforces code‑handling rules.<br/><br/>**PR.PS-06** (*Services/processes are validated to comply with security requirements before execution*). <br/>Code must meet policy + pipeline security gates before deployment.
**4. Standardize secure dev pipelines**<br/><br/> Supply chain protections are maturing: Internal artifact feeds are broadly  adopted and Component Governance runs by default. AI agents now  remediate open-source vulnerabilities asynchronously, reducing latency  between detection and resolution. These steps deliver significant gains  in security posture and operational resilience, ensuring the engineering  system maintains high standards across the software supply chain.  | **Use least privilege**: Restrict secret access. Avoid hard‑coded or persistent credentials.<br/><br/>**Assume breach**: Treat every secret as potentially compromised unless strongly guarded. | **PR.DS-02** (*Data is protected when stored*). <br/> Secure storage for build artifacts and secrets.<br/><br/>**PR.DS-10** (*Access to data is monitored*). <br/> Monitoring pipeline artifacts and logs<br/><br/>**PR.IR-01** (*Processes prepare for effective incident response*). <br/> Pipelines include logging, alerting, rollback, provenance.<br/><br/>**PR.PS-06** (*Processes/services are checked against security requirements before execution)*. <br/> Pipelines enforce mandatory security gates.
**5. Protect the software supply chain**<br/><br/>Ensure identity tokens are protected with stateful and duration validation. | **Verify explicitly**: Fully validate identity tokens at every enforcement point.<br/><br/>**Assume breach**: Ensure invalid or malformed tokens are rejected. | **GV.SC-01** (*Supply chain risk governance is established*).<br/><br/>**GV.SC-02** (*Suppliers and dependencies are identified*).<br/><br/>**GV.SC-03** (*Suppliers are evaluated for risk*).<br/><br/>**GV.SC-04** (*Security requirements for suppliers are established*).<br/><br/>**GV.SC-07** (*Supply chain components are monitored for risk*).<br/><br/>**GV.SC-09** (*Suppliers/components are validated to meet requirements)*.<br/><br/>**ID.RA-10** (*Risks from suppliers and dependencies are assessed*).<br/><br/>**PR.PR-06** (*Processes/services are validated to meet security requirements before execution*).



## Next steps

- [Review the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in What's New.
- Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).