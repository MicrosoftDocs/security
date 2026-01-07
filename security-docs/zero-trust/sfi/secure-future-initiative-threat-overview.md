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
- Pillar objectives map to [Zero Trust principles](../zero-trust-overview.md), and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms}(secure-future-initiative-overview.md#nist-functions) to help as you review the table.


## Pillar and objectives 

The aim of this pillar is to continuously monitor and rapidly detect security threats. Focus is on on proactive, intelligence-driven detection to surface attacker behavior early,  and enable rapid coordinated investigation across all business areas. 

Microsoft objectives and Zero Trust/NIST mapping for this pillar are summarized in the following table.


**Objective** |  **Zero Trust** | **NIST mapping**
--- | --- | --- 
**1. Centralize telemetry and infrastructure tracking**<br/><br/>Maintain a current resource inventory across Microsoft production infrastructure and services. | **Verify explicitly**: Asset inventories and relevant logs provide the factual baseline required to continuously validate what exists and what should be monitored. accurate inventories privent blind spots and ensure decision are based on correct and up-to-date assets.<br/><br/>**Assume breach**: High-impact assets are prioritized for monitoring because compromise is assumed to be possible and impactful. | **ID-AM-01** (*Inventories of hardware managed by the organization are maintained*).<br/>Maintaining a complete inventory of physical infrastructure ensures defenders know which production assets must be monitored and protected.<br/><br/>**ID-AM-02** (*Inventories of software, services, and systems managed by the organization are maintained*).<br/>Software and service inventories enable comprehensive telemetry collection across production environments.<br/><br/>**ID-AM-05** (*Assets are prioritized based on classification, criticality, resources, and impact on the mission*).<br/>Asset prioritization ensures monitoring and protection focus on the most critical production components.<br/><br/>**PR.PS-04** (*Log records are generated and made available for continuous monitoring*).<br/>Asset logging enables production systems to generate the telemetry required for threat detection. 
**2. Security log retention standards**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available. | **Verify explicitly**: Retained logs allow validation of historical activity and investigative accuracy. You can validate who did what and when, and validate anomalous or malicious behavior.<br/><br/>**Assume breach**: Long retention supports investigation of blended or persistent attack scenarios, even when attackers evade initial controls. External dependencies are monitored with the expectation that they might introduce risk. | **PR.PS-04** (*Log records are generated and made available for continuous monitoring*).<br/>Consistent log generation ensures that data exists to be retained and analyzed over time.<br/><br/>**DE.CM-01** (*Networks and network services are monitored to find potentially adverse events*).<br/>Network logs retained over time support detection of patterns and delayed threat discovery.<br/><br/>**DE.CM-02** (*The physical environment is monitored to find potentially adverse events*).<br/>Physical access logs contribute to long-term correlation of cyber and physical threats.<br/><br/>**DE.CM-03** (*Personnel activity and technology usage are monitored to find potentially adverse events*).<br/>User and system activity logs provide evidence for insider and credential-based threat detection.<br/><br/>**DE.CM-06** (*External service provider activities and services are monitored to find potentially adverse events*).<br/>Retained third-party activity logs support supply-chain threat detection and accountability.<br/><br/>**DE.CM-09** (*Computing hardware and software, runtime environments, and their data are monitored to find potentially adverse events*).<br/>Endpoint and runtime telemetry retention enables forensic investigation and threat hunting.
**3. Centralized access to security logs**<br/><br/>Retain security logs for at least two years, and make six months of appropriate logs available. | **Verify explicitly**: Centralized visibility enables validation across the entire environment.<br/><br/>**Assume breach**: Multi-source correlation is required when attackers operate across systems. | **PR.PS-04** (*Log records are generated and made available for continuous monitoring*)<br/> Centralization requires logs to be consistently generated and accessible from production systems.<br/><br/>**DE.AE-03** (*Information is correlated from multiple sources*)<br/>Centralized access enables correlation across network, identity, endpoint, and cloud telemetry.
**4. Rapid anomaly detection and response**<br/><br/>Detect attacks quickly, and minimize the time in which attackers have access to internal resources. | **Verify explicitly**: Detection decisions are made on analyzed, validated evidence. Categorizing events ensures decisions are repeatable.<br/><br/>**Assume breach**: Multi-source correlation is required when attackers operate across systems. |**DE.AE-02** (*Potentially adverse events are analyzed to better understand associated activities*).<br/>Analysis transforms raw signals into actionable indicators of compromise.<br/><br/>**DE.AE-03** (*Information is correlated from multiple sources*).<br/>Correlation accelerates detection of complex, cross-domain attacks.<br/><br/>**DE.AE-04** (*The estimated impact and scope of adverse events are understood*).<br/>Understanding scope and impact enables faster prioritization of response actions.<br/><br/>**DE.AE-06** (*Adverse events are categorized based on established classifications*).<br/>Classification supports consistent triage and escalation during active threats.<br/><br/>**DE.AE-07** (*Events are analyzed to support determining the root cause of cybersecurity incidents*).<br/>Root-cause analysis enables durable remediation and prevention.<br/><br/>**RS.CO-02** (*Internal and external stakeholders are notified of incidents*).<br/>Notifications ensure rapid coordination once anomalies are confirmed.<br/><br/>**RS.MI-01** (*Incidents are contained, eradicated, and mitigated consistent with response plans*).<br/>Detected anomalies lead directly to mitigation and containment actions.<br/><br/>**RS.MI-02** (*Incident response activities are tracked and communicated*).<br/>Tracking ensures response actions are coordinated, auditable, and effective.


## Next steps

- [Review the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in What's New.
- Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).

