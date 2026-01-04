---
title: Protect networks in the Microsoft Secure Future Initiative (SFI)
description: Learn how to protect networks in Microsoft's Secure Future Initiative (SFI).
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

# Overview - Protect networks in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. SFI is build upon:

- A set of security principles that drive the way in which we innovate on security design, implement those innovations into Microsoft products as secure defaults and standards, and provide internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).

This article summarizes the "Protect networks" SFI pillar.

## Before you start

- [Learn about](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars.
- [Review and track the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in the SFI What's New article.
- Pillar objectives map to [Zero Trust principles](zero-trust/zero-trust-overview), and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms](secure-future-initiative-overview.md#nist-functions) to help as you review the table.


## Pillar and objectives 

The aim of the "Protect networks" pillar is to limit adversary movement and unauthorized access across corporate networks. Networks are segmented and isolated with fine-grained network controls. Every connection is verified, controlled, and continuously monitored.

Microsoft objectives and Zero Trust/NIST mapping for this pillar are summarized in the following table.

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Inventory and security standards**<br/><br/>Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations.  | **Verify explicitly**: Know what devices are present and who/what they connect to.<br/><br/>**Assume breach**: Full inventory supports detection and containment of breaches. | **ID.AM-01**:*Physical devices and systems within the organization are inventoried*. All network devices are inventoried and tracked, recognized, managed, and governed.<br/><br/> **ID.AM-03**: *Assets are classified—consistent with organizational risk strategy*. Networks and infrastructure are inventoried and classified. <br/><br/> **PR.AA-05**: *Access permissions and authorizations are managed, enforced, and periodically verified*. SFI applied security standards to network infrastructure.<br/><br/> **PR.PS-01**-*Assets are formally evaluated to ensure they meet security, compliance, and resilience requirements before being approved for use*. Network assets are only allowed when they pass baseline security requirements.<br/><br/> **PR.PS-04**:*Assets are evaluated and validated against security requirements before being authorized for use*. Network infrastructure must meet SFI security standards before use.<br/><br/> 
**2. Network isolation**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. |  **Verify explicitly**: Authenticate and authorize network flows before allowing communication. <br/><br/>**Use least privileged access**: Restrict lateral movement and limit network access rights.<br/><br/>**Assume breach**: Assume attackers may be in the network; isolate segments for containment. | **PR-IR-01**- *Processes are established to prepare for incident response and reduce potential impact*.<br/><br/>**PR-PS-01**: *Security configuration requirements are established and applied*. Network isolation requires enforcing standardized network‑security baselines (segmentation rules, ACLs, routing controls, boundary protections).<br/><br/>**PR-PS-04**: *Assets are validated to meet security requirements before being authorized for use*. Network segments, gateways, and boundary systems must meet SFI isolation standards (hardening, compliance, segmentation posture) before being allowed to connect to production networks.
**3. Secure customer cloud networks**<br/><br/>Accelerate adoption of network security perimeter (NSP) to place entries resources under modern perimeter enforcement and segmentation to ensure network traffic is validated and only allowed where necessary to reduce the risk of lateral movement and unauthorized access.   | **Verify explicitly**: NSP enforces strong validation of traffic entering protected segments. <br/><br/>**Use least privileged access**: Only necessary traffic is allowed to traverse network boundaries.<br/><br/>**Assume breach**: Perimeter enforcement assumes threat presence and restricts spread. | **PR.IR-01**: *PProcesses are established to prepare for incident response and reduce potential impact*. Network hardening and isolation of customer cloud networks reduce blast radius and ensure Microsoft can contain incidents quickly by limiting pivot paths into or across customer environments.<br/><br/>**PR-PS-01**: *Security configuration requirements are established and applied.* Customer cloud networks must meet SFI security baselines (segmentation, routing controls, firewall posture, logging, access restrictions) before being connected or allowed to serve production workloads.



## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.