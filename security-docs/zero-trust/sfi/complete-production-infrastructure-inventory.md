---
title: Complete production infrastructure inventory
description: Complete production infrastructure inventory is part of the monitor and detect threats pillar of the Secure Future Initiative (SFI), focusing on maintaining a complete, accurate, and close to real-time inventory of all production assets. 
ms.date: 08/05/2025
ms.service: security
author: brendacarter
ms.author: bcarter
ms.topic: conceptual
ms.collection: 
  - highpri
  - zerotrust
  - sfi-zerotrust
---

# Complete production infrastructure inventory (Secure Future Initiative)

**Pillar name: Monitor and detect threats**<br>  
**Pattern name: Complete production infrastructure inventory**

Complete production infrastructure inventory is part of the Monitor and Detect Threats pillar of the Secure Future Initiative (SFI). This pillar is focused on ensuring that Microsoft’s environments provide high-fidelity telemetry, comprehensive visibility, and advanced detection capabilities to identify and respond to evolving threats.

A complete, accurate, and close to real-time inventory of all production assets is foundational to powering this pillar—enabling consistent policy enforcement, trusted telemetry, and accelerated threat detection and response.

## Context and problem

As enterprise environments grow increasingly complex—with a mix of legacy systems, cloud workloads, APIs, and user identities—maintaining visibility across the entire production infrastructure becomes increasingly difficult.

Without complete real-time understanding of what exists in the environment:

- Threats can go undetected due to telemetry blind spots
- Security policies may be inconsistently applied
- Misconfigured or unmanaged assets may introduce avoidable vulnerabilities
- Applications and services can persist long after they are abandoned, further expanding the attack surface

Incomplete asset inventories contribute to:

- Delayed threat detection
- Inconsistent enforcement of Zero Trust policies
- Operational inefficiencies

Even at Microsoft’s scale, it became clear that incomplete asset inventories were contributing to delayed detection, inconsistent enforcement of Zero Trust policies, and operational inefficiencies.

Treating infrastructure visibility as a core security priority becomes essential to eliminating blind spots and reducing risk.

## Solution

To address this challenge, Microsoft launched the Complete production infrastructure inventory objective under the Secure Future Initiative. The goal: continuously maintain a real-time inventory of 100% of production infrastructure assets—including cloud, on-premises, hybrid, and containerized environments. This effort required significant cross-team coordination and investment in scalable automation.

From it, Microsoft:

- Defined and discovered all production assets, including devices, services, APIs, workloads, and third-party integrations
- Centralized inventory management in a system capable of tracking changes in near-real time
- Extended audit log and telemetry coverage to ensure all assets emitted standardized logs via centrally managed agents
- Integrated the inventory system with detection platforms, enriching SIEM and threat analytics with real-time metadata
- Remediated unused applications—over 730,000 apps so far have been flagged and safely removed using automated log analysis on Azure Kubernetes Service, hosted in confidential containers
- Implemented an application remediation workflow for unused applications that have not demonstrated activity or maintenance and were flagged and evaluated for safe removal

To date, Microsoft centrally tracks more than 97% of production infrastructure assets. In addition, 99% of network devices and more than 95% of nodes/machines have central security log collection with a two-year retention policy enforced.

## Guidance

Organizations can adopt a similar pattern using the following actionable practices:


|Use case|Recommended action |Resource |
|---|---|---|
| Asset identification   | <ul><li>Inventory all devices, services, APIs, workloads, and third-party applications</li></ul>|[Critical asset management](https://learn.microsoft.com/security-exposure-management/critical-asset-management) |
| Real-time asset detection |<ul><li>Use automated discovery tools and IP attribution systems to detect assets in real time</li></ul>| [Critical asset management](https://learn.microsoft.com/security-exposure-management/critical-asset-management)  |
| Centralized inventory |<ul><li>Consolidate records into a system that supports classification and lifecycle visibility</li><li>Establish continuous update mechanism</li></ul>| <ul><li><a href="https://learn.microsoft.com/dynamics365/supply-chain/asset-management/setup-for-objects/object-stages">Asset lifecycle states</a></li><li><a href="https://learn.microsoft.com/microsoft-365-apps/updates/overview-update-process-microsoft-365-apps">Overview of the update process for Microsoft 365 Apps</a></li></ul>  |
| Telemetry standardization |<ul><li>Deploy centrally managed agents to enforce consistent logging</li><li>Confirm API logging coverage and track observability gaps</li></ul>| <ul><li><a href="https://learn.microsoft.com/azure/logic-apps/enable-enhanced-telemetry-standard-workflows?tabs=portal">Set up and view enhanced telemetry in Application Insights for Standard workflows in Azure Logic Apps</a></li><li><a href="https://learn.microsoft.com/azure/azure-monitor/app/data-model-complete">Application Insights telemetry data model</a></li><li><a href="https://learn.microsoft.com/azure/api-management/api-management-howto-use-azure-monitor">Tutorial: Monitor published APIs</a></li></ul> |
| Threat detection integration |<ul><li>Correlate logs with inventory metadata to improve detection fidelity</li><li>Use analytics and ML to proactively identify anomalies</li></ul>| <ul><li><a href="https://www.microsoft.com/security/business/siem-and-xdr/microsoft-defender-threat-intelligence">Microsoft Defender Threat Intelligence</a></li><li><a href="https://learn.microsoft.com/azure/azure-monitor/app/data-model-complete">Application Insights telemetry data model</a></li><li><a href="https://learn.microsoft.com/azure/security/fundamentals/threat-detection">Microsoft Defender Threat Intelligence</a></li></ul> |
| Unused app remediation   |<ul><li>Identify inactive apps using usage and sign-in logs</li><li>Validate with service owners and allow for business-critical exceptions</li><li>Apply soft deletion with a grace period, followed by permanent removal</li><li>Run sensitive workloads in a trusted execution environment</li></ul>| <ul><li><a href="https://learn.microsoft.com/entra/identity/monitoring-health/recommendation-remove-unused-credential-from-apps?tabs=microsoft-entra-admin-center">Microsoft Entra recommendation: Remove unused credentials from apps</a></li><li><a href="https://learn.microsoft.com/entra/identity/monitoring-health/recommendation-remove-unused-apps?tabs=microsoft-entra-admin-center">Microsoft Entra recommendation: Remove unused applications</a></li><li><a href="https://learn.microsoft.com/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview">Data retention, deletion, and destruction in Microsoft 365</a></li><li><a href="https://learn.microsoft.com/azure/confidential-computing/quick-create-confidential-vm-portal">Quickstart: Create confidential VM on in the Azure portal</a></li></ul>|
 
## Outcomes

Microsoft’s implementation of a centralized, comprehensive infrastructure inventory has led to:

- Faster threat detection and incident response due to improved signal clarity
- Consistent enforcement of Zero Trust policies across all managed assets
- Elimination of outdated or orphaned applications, reducing attack surface area
- Proactive posture management rooted in trusted, real-time telemetry

### Benefits

- 97% continuous tracking coverage across production environments
- Faster threat detection and incident response due to improved signal clarity
- Consistent Zero Trust enforcement across all managed assets
- Reduced attack surface by eliminating outdated or orphaned applications
- Trusted telemetry for proactive posture management

### Trade-offs

- Requires significant engineering investment in automation and telemetry standardization
- Demands cultural change to prioritize asset visibility across teams
- Restricts use of unmanaged or personal devices in favor of domain-joined systems
- Introduces risk of disruption if inactive but critical apps were removed without validation

## Key success factors

To track success, measure the following:

- Percentage of production assets with full inventory coverage
- Number of unmanaged or orphaned systems remediated
- Coverage percentage of infrastructure telemetry logging
- Time-to-detect and time-to-respond metrics before and after inventory implementation
- Volume of unused applications safely remediated per quarter

## Summary

A complete production infrastructure inventory is a foundational enabler of **Secure by Design**, **Secure by Default**, and **Secure Operations** in Microsoft’s Secure Future Initiative.

Organizations that commit to real-time asset visibility and telemetry standardization can strengthen their security posture, reduce operational risk, and enable faster, more effective response. Building a complete infrastructure inventory is not only the best practice; it’s a critical requirement for resilient, scalable cybersecurity in the modern enterprise.

**Start building your inventory today—and enable threat detection that works with clarity, consistency, and confidence.**
