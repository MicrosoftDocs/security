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
- [Get a list of NIST categories and acronyms}(secure-future-initiative-overview.md#nist-functions) to help as you review the table.


## Pillar and objectives 

The aim of the "Protect networks" pillar is to limit adversary movement and unauthorized access across corporate networks. Networks are segmented and isolated with fine-grained network controls. Every connection is verified, controlled, and continuously monitored.

Microsoft objectives for this pillar are summarized in the following table. 

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Complete network device inventory and asset lifecycle management**<br/><br/>Secure Microsoft production networks and systems connected to networks with improved network isolation, monitoring, accurate inventory, and secure operations.  | **Verify explicitly**: Know what devices are present and who/what they connect to.<br/><br/>**Assume breach**: Full inventory supports detection and containment of breaches. | **ID.AM-02**: Inventory of organizational resources. All network devices are inventoried and tracked. 
**2. Strengthen security through enhanced network isolation and controls**<br/><br/>Apply identity-aware network isolation and microsegmentation to Microsoft production environments, creating additional layers of defense against attackers. |  **Verify explicitly**: Authenticate and authorize network flows before allowing communication. <br/><br/>**Use least privileged access**: Restrict lateral movement and limit network access rights.<br/><br/>**Assume breach**: Assume attackers may be in the network; isolate segments for containment. | **PR-PS-02**: Platform Security. Secure network platform configurations help enforce isolation and protect network boundaries. (Platform security covers network protection technologies such as segmentation firewalls, ACLs, and infrastructure controls.)
**3. Accelerate adoption of Network Security Perimeter (NSP)**<br/><br/>Place entries resources under modern perimeter enforcement and segmentation to ensure network traffic is validated and only allowed where necessary to reduce the risk of lateral movement and unauthorized access.   | **Verify explicitly**: NSP enforces strong validation of traffic entering protected segments. <br/><br/>**Use least privileged access**: Only necessary traffic is allowed to traverse network boundaries.<br/><br/>**Assume breach**: Perimeter enforcement assumes threat presence and restricts spread. | **PR-PS-01**: Platform Security. NSP technologies and perimetral controls are part of secure platform defenses. (These technologies enforce network segmentation and traffic policies to protect infrastructure.)
**4. Improve network acccess controls and protective technologies**<br/><br/>Strengthen network defenses with modern firewalling, segmentation policies, and platform-level enforcement, ensuring that only authorized traffic can flow and that potential breaches are contained. | **Verify explicitly**: Access control policies verify traffic flows and endpoints. <br/><br/>**Use least privileged access**: Policy enforcement limits access to minimal required paths.<br/><br/>**Assume breach**: Contain attacks via strong network controls and visibility. | **PR.AA-03**: Access enforcement. Enforce network access decisions.br/><br/> **PR.PS-01**: Platform Security. Infrastructure (firewalls, NSGs, segmentation) enforced at platform level.

## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.