---
title: Accelerate response and remediation in the Microsoft Secure Future Initiative (SFI)
description: Learn how to accelerate response and remediation in Microsoft's Secure Future Initiative (SFI).
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

# Overview - Accelerate response and remediation

The [Secure Future Initiative (SFI) initiative](secure-future-initiative-overview.md) is a multiyear, cross-Microsoft initiative to increasingly secure the way in which Microsoft designs, builds, tests, and operates its products and services. SFI is build upon:

- A set of security principles that drive the way in which we innovate on security design, implement those innovations into Microsoft products as secure defaults and standards, and provide internal and external security guidance. [Learn more](secure-future-initiative-overview.md#security-principles).
- A set of prioritized security pillars and objectives. [Learn more](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist).

This article summarizes the "Accelerate response and remediation" SFI pillar.

## Before you start

- [Learn about](secure-future-initiative-overview.md#sfi-pillars-zero-trust-and-nist) the SFI pillars.
- [Review and track the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in the SFI What's New article.
- Pillar objectives map to [Zero Trust principles](../zero-trust-overview.md), and to  [NIST CSF functions and categories](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf).
- [Get a list of NIST categories and acronyms](secure-future-initiative-overview.md#nist-functions) to help as you review the table in this article.


## Pillar and objectives 

The aim of this pillar is to quickly contain threats, restore trust, and improve resilience. It aims to minimize the impact and duration of security events and attacker dwell time in internal networks.


Microsoft objectives and Zero Trust/NIST mapping for this pillar are summarized in the following table.

**Objective** | **Zero Trust** | **NIST mapping**
--- | --- | ---
**1. Accelerate vulnerability mitigation**<br/><br/>Reduce "Time to Mitigation" for high-severity cloud security vulnerabilities with accelerated response. | **Verify explicitly**: Make decisions based on continuously validated vulnerability signals to ensure that mitigation actions are timely and accurate.<br/><br/>**Assume breach**: Remediate with the assumption that vulnerabilities might already be exploited. | **ID.RA-01** (*Vulnerabilities in assets are identified, validated, and recorded*). <br/> Ensures that vulnerabilities are accurately identified and validated so mitigation efforts focus on confirmed, high-risk exposures.<br/><br/>**RS.AN-03** (*Analysis is performed to determine what has taken place during an incident and the root cause of the incident*).<br/>MRoot-cause analysis informs remediation by clarifying how vulnerabilities are exploited and what controls must be strengthened to prevent recurrence.<br/><br/>**RS.MA-02** (*Incident reports are triaged and validated*).<br/>Vulnerability-driven incidents are triaged and validated to ensure remediation actions are based on reliable incident data.<br/><br/>**RS.MA-03** (*Incidents are categorized and prioritized*).<br/>Categorization and prioritization ensure mitigation efforts address the most critical vulnerabilities first, reducing overall risk exposure.<br/><br/>**RC.RP-01** (*Recovery plan is executed*).<br/>Recovery plans are executed to restore secure operations after vulnerabilities are mitigated or exploited.<br/><br/>**RC.RP-02** (*Recovery actions are selected, scoped, prioritized, and performed*).<br/>Recovery actions are scoped and prioritized to align remediation speed with business impact and risk severity.
**2. Transparency of cloud vulnerabilities**<br/><br/>Increase transparency of mitigated cloud vulnerabilities with the adoption and release of Common Weakness Enumeration (CWE) and Common Platform Enumeration (CPE) industry standards. Release high severity Common Vulnerabilities and Exposures (CVEs) affecting the cloud. | **Verify explicitly**: Public messaging is information by verified incident analysis, vulernability status, and remediation process. <br/><br/>**Use least privileged access**: Access to vulnerability data, reporting pipelines and disclosure mechanisms are governed and information is shared appropriately. | **ID.RA-01** (*Vulnerabilities in assets are identified, validated, and recorded*).<br/>Accurate identification and validation of cloud vulnerabilities ensures transparency is based on verified exposure rather than assumptions.<br/><br/>**RS.CO-02** (*Internal and external stakeholders are notified of incidents*).<br/>Customers and partners are notified when cloud vulnerabilities represent meaningful security risk, enabling timely defensive action.<br/><br/>**RS.CO-03** (*Information is shared with designated internal and external stakeholders*).<br/>Vulnerability information is shared in a structured and role-appropriate manner to support coordinated mitigation without unnecessary disclosure.
**3. Enhance public messaging and engagement**<br/><br/>Improve the accuracy, effectiveness, transparency, and velocity of public messaging and customer engagement. | **Verify explicitly**: Public messaging is information by verified incident analysis, vulnerability status, and remediation process so that messaging is accurate and timely. | **GV-OV-01** (*Cybersecurity risk management strategy outcomes are reviewed to inform and adjust strategy and direction*).<br/>Public messaging reflects reviewed outcomes of cybersecurity risk management activities rather than isolated technical events.<br/><br/>**GV-OV-02** (*The cybersecurity risk management strategy is reviewed and adjusted to ensure coverage of organizational requirements and risks*).<br/>Engagement activities are aligned with evolving organizational risk and stakeholder expectations.<br/><br/>**GV-OV-03** (*Organizational cybersecurity risk management performance is measured and reviewed to confirm and adjust strategic direction*).<br/>Performance metrics inform transparent communication about progress, gaps, and improvement areas.<br/><br/>**GV-RR-01** (*Organizational leadership is responsible and accountable for cybersecurity risk and fosters a culture that is risk-aware, ethical, and continually improving*).<br/>Leadership accountability ensures public engagement is credible, consistent, and aligned with organizational values.<br/><br/>**GV-RR-02** (*Roles, responsibilities, and authorities related to cybersecurity risk management are established, communicated, and enforced*).<br/>Clear ownership of communication responsibilities prevents inconsistent or unauthorized public messaging.<br/><br/>**GV-RR-03** (*Adequate resources are allocated consistent with the cybersecurity risk management strategy*).<br/>Sufficient resourcing enables sustained engagement with customers, researchers, and the broader ecosystem.<br/><br/>**RS.CO-03** (*Information is shared with designated internal and external stakeholders*).<br/>Structured information sharing supports coordinated and trustworthy public engagement during security events.<br/><br/>**RS.CO-04** (*Public updates on incident recovery are shared using approved methods and messaging*).<br/>Structured information sharing supports coordinated and trustworthy public engagement during security events.<br/><br/>**RC.CO-03** (*Recovery activities and progress in restoring operational capabilities are communicated to designated internal and external stakeholders*).<br/>Structured information sharing supports coordinated and trustworthy public engagement during security events.



## Next steps

- [Review the latest progress on pillar objectives](secure-future-initiative-whats-new.md#progress-on-pillar-objectives) in What's New.
- Learn about [adopting Microsoft SFI best practices](secure-future-initiative-adoption.md).
