---
title: Centralize access to security logs
description: Centralize access to security logs is part of the Monitor and detect threats pillar of the Secure Future Initiative (SFI). This pillar supports Microsoft environments providing high-fidelity telemetry, comprehensive visibility, and advanced detection capabilities to identify and respond to evolving threats 
ms.date: 10/03/2025
ms.service: security
author: leonyen
ms.author: lyen
ms.subservice: zero-trust
ms.topic: conceptual
ms.collection:
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Centralize access to security logs (Secure Future Initiative)

**Pillar name: Monitor and detect threats**<br />
**Pattern name: Centralize access to security logs**

## Context and problem

Security logs are one of the most critical tools for defenders—they reveal who accessed what, when, and how. Logs support continuous monitoring of threat activity, speed up incident response, and provide forensic records for security investigations.

Yet without centralization and standardization, logs can create more problems than they solve. Inconsistent formats, disparate storage locations, and variable retention periods make it difficult to quickly piece together a complete picture of an attack. At Microsoft, investigations were slowed by fragmented log sources and gaps in retention that left defenders unable to trace initial access points or lateral movement paths.

## Solution

As part of SFI, Microsoft centralized access to security logs and extended retention policies. Key measures include:

* **Standardized security logging library**: Ensures consistent data capture across services, reducing telemetry gaps.

* **Centralized log collection**: Specialized investigator accounts provide unified access to cross-service logs, simplifying correlation and speeding up investigations.

* **Extended log retention**: Audit logs retained for up to two years across Microsoft services, to enable forensic investigation of long-term attack patterns.

* **Advanced detection analytics**: Integration of machine learning and AI-powered models improves detection of complex attack techniques and reduces false positives.

* **Expanded customer logging**: Microsoft increased standard audit log retention for Microsoft 365 customers to 180 days at no cost, with options for longer retention.

## Guidance
Organizations can adopt a similar pattern using the following actionable practices:

|Use case|Recommended action |Resource |
|---|---|---|
| Standardized logging   | <ul><li>Use Microsoft Purview auditing solution for Microsoft Entra and Microsoft 365 applications logs (for example, Exchange Online, SharePoint, OneDrive).</li><li>Implement a common log library across applications and services to enforce consistent fields (identity, actions, timestamps).</li></ul>| <ul><li>[Learn about auditing solutions in Microsoft Purview](https://learn.microsoft.com/en-us/purview/audit-solutions-overview)</li><li>[Microsoft Sentinel data lake overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-lake-overview)</li></ul> |
| Central log storage |<ul><li>Use Microsoft Sentinel's data lake to transform SIEM with AI and unified security data.</li><li>Direct all security logs into a central repository, accessible to authorized investigators.</li><li>Centralize access to logs with Azure's Monitor and Log Analytics to reduce blind spots.</li>             <li>Use Microsoft Sentinel's security information and event management (SIEM) solution to enhance visibility and context for security logs and data, threat investigation, and response.</li></ul> | <ul><li>[Microsoft Sentinel data lake overview - Microsoft Security](http://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-lake-overview)</li><li>[Azure Monitor Logs](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/data-platform-logs)</li><li>[Microsoft Sentinel data connectors](https://learn.microsoft.com/en-us/azure/sentinel/connect-data-sources?tabs=defender-portal)</li><li>[Microsoft Entra security operations for infrastructure](https://learn.microsoft.com/en-us/entra/architecture/security-operations-infrastructure)</li></ul> |
| Encryption and immutable storage |<ul><li>In Azure Monitor, you can secure log data in transit and encrypt Log Analytics data at rest in Azure Storage using Microsoft-managed keys (MMK)</li><li>Encrypt logs in transit and at rest, and store them immutably to preserve forensic integrity, using Sentinel's data tiering for  cost-efficient retention.</li><li>We recommend using immutable to protect from overwrites and deletes.</li></ul>| <ul><li>[Log Analytics workspace overview](https://learn.microsoft.com/azure/azure-monitor/logs/log-analytics-workspace-overview)</li><li>[Secure your Azure Monitor deployment](https://learn.microsoft.com/azure/azure-monitor/fundamentals/best-practices-security)</li><li>[Encryption at rest in Azure Storage](https://learn.microsoft.com/azure/storage/common/storage-service-encryption#about-azure-storage-service-side-encryption)</li><li>[Immutable storage](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview)</li><li>[Manage data tiers and retention in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/manage-data-overview)</li></ul> |
| Real-time monitoring |<ul><li>Set up continuous monitoring and alerts with Azure Monitor and Microsoft Sentinel to detect suspicious activity or logging coverage gaps.</li><li>In Azure Monitor and Log Analytics, you can monitor, improve logging coverage, and alert on suspicious activities using KQL queries and alert rules</li><li>Microsoft Sentinel provides advanced monitoring and detection features such as real-time log ingestion, analytics rules to watch ingested data, log matching against threat intelligence, alert grouping into incidents, and security orchestration, automation, and response (SOAR) capabilities.</li></ul>| <ul><li>[Log queries in Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/logs/log-query-overview)</li><li>[Azure Monitor diagnostics settings](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/diagnostics-settings-policies-deployifnotexists)</li><li>[Monitor Azure resources with Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/platform/monitor-azure-resource)</li><li>[Log ingestion with data connectors](https://learn.microsoft.com/azure/sentinel/connect-data-sources)</li><li>[Detect and analyze anomalies using KQL in Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/logs/kql-machine-learning-azure-monitor)</li><li>[Quick threat detection with near-real-time (NRT) analytics rules in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/near-real-time-rules)</li></ul>|
| Advanced analytics |<ul><li>Correlate logs across services using ML/AI and integrate with threat intelligence feeds.</li><li>Correlate logs in Azure Monitor and Log Analytics using KQL queries to connect signals across data sources.</li><li>Apply advanced analytics in Microsoft Sentinel with prebuilt rule libraries that map to common attack patterns, user and entity behavior analytics (UEBA) for anomaly detection, AI-powered alert correlation, ML-driven anomaly detection, and logs enriched with threat intelligence.</li></ul>| <ul><li>[Microsoft Sentinel documentation](https://learn.microsoft.com/en-us/azure/sentinel/)</li><li>[Threat detection in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/threat-detection)</li><li>[Advanced threat detection with User and Entity Behavior Analytics (UEBA) in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics)</li><li>[Alert correlation in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/relate-alerts-to-incidents)</li><li>[Threat intelligence - Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/understand-threat-intelligence)</li></ul> |
| Review cadence  |<ul><li>Conduct quarterly reviews to validate coverage, retention compliance, and pipeline integration.</li><li>Optimize SOC processes with Microsoft best practices and guidance on security operations.</li></ul>| <ul><li>[Azure Monitor best practices](https://learn.microsoft.com/en-us/azure/azure-monitor/best-practices-security#log-ingestion-and-storage)</li><li>[Optimize security operations](https://learn.microsoft.com/en-us/azure/sentinel/soc-optimization/soc-optimization-access?tabs=defender-portal)</li></ul> |

## Benefits 

* **Improved visibility:** Provides defenders with a unified view of activity across identities, infrastructure, applications and endpoint devices.
* **Faster investigations:** Investigators can correlate events across services without manual searches or format conversion.
* **Forensic readiness:** Extended retention ensures defenders can analyze long-term attack campaigns.
* **Proactive detection:** AI-driven analytics surface emerging attack patterns earlier.
* **Regulatory alignment:** Supports compliance with standards requiring centralized, retained audit evidence.

## Trade-offs 

* **Increased storage costs:** Extending retention and centralizing logs requires scalable infrastructure.
* **Access governance complexity:** Centralized investigator accounts must be strictly controlled to prevent misuse.
* **Operational overhead:** Teams must maintain log libraries, pipelines, and monitoring tools across services.
* **Signal-to-noise balance:** Centralized logging increases data volume, requiring investment in advanced filtering and analytics.

## Key success factors

To track success, measure the following: 
* Percentage of services using the standardized logging library.
* Number of pipelines and services successfully forwarding logs to the central repository.
* Mean time to investigate (MTTI) reduced by centralized access.
* Compliance with two-year audit log retention standard.
* Detection accuracy improvements from AI/ML-enhanced analytics.

## Summary

Centralizing access to security logs transforms fragmented telemetry into actionable intelligence. By standardizing log formats, consolidating collection, extending retention, and applying AI-driven analytics,
Microsoft has improved both the speed and effectiveness of its threat detection and investigation.

Organizations can adopt this approach by ensuring consistent log formats, enforcing central storage and immutability, extending retention for forensic readiness, and integrating logs with advanced analytics platforms. These steps enable defenders to monitor and detect threats with clarity and precision---turning logs from scattered records into a powerful, unified security capability.

**Centralize your security logs today to reduce blind spots, accelerate investigations, and stay ahead of evolving threats.**
