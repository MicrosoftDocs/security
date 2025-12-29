---
title: Monitor and detect threats in the Microsoft Secure Future Initiative (SFI)
description: Learn how to monitor and detect threats in Microsoft's Secure Future Initiative (SFI).
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

# Overview - Monitor and detect threats in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. SFI is build upon:

- A set of security principles that drive the way in which we innovate on security design, implement those innovations into Microsoft products as secure defaults and standards, and provide internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).
- 
This article summarizes the "Monitor and detect threats" SFI pillar.

## Before you start

- [Learn about](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars.
- [Review and track the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in the SFI What's New article.
- Pillar objectives map to [Zero Trust principles](zero-trust/zero-trust-overview), and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms}(secure-future-initiative-overview.md#nist-functions) to help as you review the table.


## Pillar and objectives 

The aim of this pillar is to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. 

Microsoft objectives for this pillar are summarized in the following table. 


**Objective** |  **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Centralize telemetry and infrastructure tracking**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services. | **Verify explicitly**:Ensure logging and telemetry originate from authenticated, trusted sources.<br/><br/>**Assume breach**: Centralized logs support detection even when attackers evade initial controls.| **ID.AM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **Detect:Continuous Monitoring (DE-AM-02)**: Monitoring processes. Centralized telemetry supports continuous observation.
**2. Retain logs for forensic analysis and trending**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available. | **Verify explicitly**: Retained logs allow verification of past events and patterns.<br/><br/>**Assume breach**: Long retention ensures detection windows cover advanced stealth techniques.| **DE.CM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **DE/DP-01



## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.

