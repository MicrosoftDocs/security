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

# Monitor and detect threats in SFI

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) launched in November 2023 as a multiyear effort to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services.

SFI architecture design focuses on a set of security principles that are adopted and integrated into Microsoft culture and governance. These security principles are applied to a set of engineering pillars by means of processes, standards, and continuous improvements.

This article summarizes the "Protect identities and secrets" SFI pillar.

## Before you start

- [Review](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars
- [Review tthe latest progress on pillar objectives](secure-future-initiative-whats-new.md#pillar-progress) in What's New.


## Pillar and objectives 

The aim of this pillar is to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. 

Microsoft objectives for this pillar are summarized in the following table. You can see how each objective maps toZero Trust principles, and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).


**Objective** |  **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Centralize telemetry and infrastructure tracking**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services. | **Verify explicitly**:Ensure logging and telemetry originate from authenticated, trusted sources.<br/><br/>**Assume breach**: Centralized logs support detection even when attackers evade initial controls.| **ID.AM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **Detect:Continuous Monitoring (DE-AM-02)**: Monitoring processes. Centralized telemetry supports continuous observation.
**2. Retain logs for forensic analysis and trending**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available. | **Verify explicitly**: Retained logs allow verification of past events and patterns.<br/><br/>**Assume breach**: Long retention ensures detection windows cover advanced stealth techniques.| **DE.CM-02**: Inventory of organizational resources: Maintain a complete view of monitored assets.<br/><br/>** **DE/DP-01



## Next steps

[Learn about](secure-future-initiative-guidance.md) adopting Microsoft SFI best practices.

