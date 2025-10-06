---
title: Security log retention standards (Secure Future Initiative) – Zero Trust
description: Security log retention standards are part of the monitor and detect threats pillar of the Secure Future Initiative (SFI), focusing on standardizing, centralizing, and extending Microsoft's logging processes.
ms.date: 08/05/2025
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

# Security log retention standards (Secure Future Initiative)

**Pillar name: Monitor and detect threats**<br>
**Practice name: Security log retention standards** 

Security logs are crucial for threat detection and incident investigation, but their efficacy is dependent on various factors, including format and retention period. To improve threat detection and incident investigation measures, the Security log retention standards practice enhances security logging by standardizing formats, centralizing storage, and extending retention periods.

## Context and problem

Security logs play a critical role in detecting threats, investigating incidents, and maintaining compliance. However, Microsoft identified several challenges that limited the effectiveness of security logging across services:

- Inconsistent logging formats made it difficult for investigators to quickly interpret and correlate data.
- Disparate log storage created delays in threat response by requiring investigators to manually search across systems.
- Variable retention periods left gaps in forensic analysis, preventing a full understanding of how attacks unfolded over time.

Without standardized log formats, centralized log access, and consistent retention of logs, incident responders faced significant cognitive load, leading to longer investigation cycles and reduced detection efficacy.

## Solution

To address these issues, Microsoft implemented a comprehensive overhaul of its security logging approach, focused on three key areas: standardization, centralization, and extended retention. These efforts were carried out under the Secure Future Initiative (SFI) as part of the monitor and detect threats pillar.

Key components of Microsoft’s approach included:

- Developed a standard security logging library to unify logging practices across services, reducing gaps in telemetry and enabling consistent data formatting.
- Centralized log access by establishing a cross-service log management platform, which empowered security investigators with unified access and visibility.
- Extended log retention periods to two years for most Microsoft-used service instances to enable long-term forensic investigations and detection of persistent threats.
- Integrated logs with advanced threat detection systems, including machine learning models and AI-driven analytics, to identify anomalies and accelerate detection.

Together, these efforts allow for more efficient and scalable security operations across Microsoft’s environments while enhancing transparency for external customers through expanded logging capabilities.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Standardize log generation   |<ul><li>Adopt a centralized logging library with consistent fields.</li><li>Identify and fill telemetry gaps across services and APIs.</li></ul> | [Azure security logging and auditing](/azure/security/fundamentals/log-audit)  |
| Centralize storage and access   | <ul><li>Use a centralized log management system (e.g., Azure Data Explorer and Sentinel).</li><li>Ensure security teams have appropriate access to view and query relevant logs from a unified interface.</li></ul> | <ul><li><a href="/azure/azure-monitor/">Getting started with Azure Monitor</a></li><li><a href="/azure/sentinel/">Microsoft Sentinel documentation</a></li></ul> |
| Extend and automate retention    | <ul><li>Define retention periods based on threat profiles, risk tolerance, and compliance.</li><li>Secure logs using encryption, immutability, and access controls to prevent tampering.</li><li>Automate retention and deletion workflows to ensure consistency and compliance.</li></ul> | <ul><li><a href="/azure/sentinel/log-plans">Log retention plans in Microsoft Sentinel</a></li><li><a href="/defender-xdr/data-privacy">Data security and retention in Microsoft Defender XDR</a></li></ul> |
| Improve detection through analytics   | <ul><li>Correlate logs with threat intelligence feeds and enrich them with contextual metadata.</li><li>Use machine learning and anomaly detection tools (e.g., Microsoft Sentinel) to identify emerging threats and suspicious behaviors.</li><li>Review and refine detection models regularly to keep pace with evolving attack techniques.</li></ul> | [Work with anomaly detection analytics rules in Microsoft Sentinel](/azure/sentinel/work-with-anomaly-rules)  |
| Monitor and review logging coverage   | <ul><li>Inventory all services and ensure full API logging coverage.</li><li>Perform regular audits to assess logging completeness, identify regressions, and enforce policy compliance.</li></ul> | [Azure API Center](/azure/api-center/overview)  |

## Outcomes

Microsoft’s enhanced log retention standards approach has led to:

### Benefits

- Higher signal fidelity: Standardized logs eliminate noise and streamline detection pipelines.
- Improved investigation speed: Centralized access reduces time spent locating and interpreting logs.
- Enhanced forensic readiness: Longer retention ensures full incident timelines are available.
- Scalable analytics: Consistent formats enable machine learning to identify suspicious behaviors more effectively.

### Trade-offs

- Significant engineering effort to update telemetry libraries and log generation across distributed services.
- Coordination across teams to enforce adherence to new standards and retention policies.
- Investment in scalable, secure infrastructure to support centralized storage and long-term retention of log data.
- Acceptance of higher storage and compute costs associated with extended log retention, which are incurred if customers go beyond default limits.

## Key success factors

To track the effectiveness of your log retention strategy, measure:

- Percentage of services and APIs using the standard logging library
- Percentage of centralized logging coverage across environments
- Average time to detect and respond to threats before and after standardization
- Log retention duration compliance with internal policies and regulations
- Accuracy and volume of threat detections triggered from log analysis

## Summary

A comprehensive logging strategy is a foundational enabler of Secure by Design, Secure by Default, and Secure Operations in Microsoft’s Secure Future Initiative.

Microsoft’s experience shows that with the right patterns and practices:

> Organizations that implement standardized, centralized, and extended log retention can significantly improve their threat detection capabilities, accelerate investigations, and maintain a stronger security posture. Security log retention is not just a compliance checkbox—it’s a strategic investment in operational resilience.

**Start standardizing and scaling your log retention efforts today—and give your security teams the visibility and speed they need to stay ahead of evolving threats.**
